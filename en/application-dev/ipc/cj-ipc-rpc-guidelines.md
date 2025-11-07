# IPC and RPC Communication Development Guide

## Scenario Description

Client and server communicate using message queues.

## Client-Server Communication Example

- Define the Server

```cangjie
class Stub <: RemoteObject {
    public init(descriptor: String) {
        super(descriptor)
    }

    public func onRemoteMessageRequest(code: Int32, data: MessageSequence, reply: MessageSequence, option: MessageOption): Bool {
        match(code) {
            case 1 =>
                // Read corresponding data in the order written by the client, specific logic depends on business requirements
                // This example corresponds to the client message sending shown later
                let ret = MyParcelable()
                data.readParcelable(ret)
                // Send data to client
                let ashmem = Ashmem.create("ashmem", 1024)
                ashmem.writeDataToAshmem([1, 2, 3], 3, 0)
                let mes = MyParcelable(1, "this is stub", ashmem)
                reply.writeParcelable(mes)
                return true
            case _ => return false
        }
    }
}

// Custom serializable object shared by server and client
class MyParcelable <: Parcelable {
    // Integer data
    var num: Int32 = 0
    // String data
    var str: String = ''
    // Anonymous shared memory object
    var ashmem: Ashmem

    init() {
        this.ashmem = Ashmem.create("ashmem", 1024)
    }

    init(num: Int32, str: String, ashmem: Ashmem) {
        this.num = num
        this.str = str
        this.ashmem = ashmem
    }
    public func marshalling(messageSequence: MessageSequence): Bool {
        messageSequence.writeInt(this.num)
        messageSequence.writeString(this.str)
        messageSequence.writeAshmem(this.ashmem)
        return true
    }
    public func unmarshalling(messageSequence: MessageSequence): Bool {
        this.num = messageSequence.readInt()
        this.str = messageSequence.readString()
        this.ashmem = messageSequence.readAshmem()
        return true
    }
}
```

- Define the Client

```cangjie
import kit.IPCKit.*

let option = MessageOption()
let data = MessageSequence.create()
let reply = MessageSequence.create()

// Prepare data to send to server
let ashmem = Ashmem.create("ashmem", 1024)
ashmem.writeDataToAshmem([3, 2, 1], 3, 0)
let mes = MyParcelable(0, "this is proxy", ashmem)
data.writeParcelable(mes)

let proxy = IRemoteObject()
proxy.sendMessageRequest(1, data, reply, option)
// Read server response data from reply
let ret = MyParcelable()
reply.readParcelable(ret)
```