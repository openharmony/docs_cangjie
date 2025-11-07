# Key Events  

Key events refer to the events triggered when components interact with input devices such as keyboards or remote controls. These events apply to all focusable components, such as Button. For components like Text and Image that are not focusable by default, key events are currently unsupported. However, support may be added in the future by setting the `focusable` property to `true`.

## Import Module  

```cangjie  
import kit.ArkUI.*  
```  

## func onKeyEvent(?(KeyEvent) -> Unit)  

```cangjie  
func onKeyEvent(event: ?(KeyEvent) -> Unit): T  
```  

**Function:**  
When the component bound to this method gains focus, a key action triggers this event.  

**System Capability:**  
SystemCapability.ArkUI.ArkUI.Full  

**Since Version:**  
22  

**Parameters:**  

| Parameter | Type | Required | Default Value | Description |  
|:---|:---|:---|:---|:---|  
| event | ?([KeyEvent](./cj-common-types.md#class-keyevent)) -> Unit | Yes | - | Callback triggered by a key action when the bound component gains focus. |  

**Return Value:**  

| Type | Description |  
|:---|:---|  
| T | Returns the generic method interface type. |