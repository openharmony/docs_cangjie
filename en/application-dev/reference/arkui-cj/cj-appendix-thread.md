# Thread Control

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

## Background

During the development of OpenHarmony applications in Cangjie, the code logic is primarily divided into two parts: UI-related logic code and UI-independent logic code.

- **UI-related logic code**: Includes UI layout description code, UI state declaration, and modification code.
- **UI-independent logic code**: All other code excluding UI-related logic code.

UI-related logic code must run on the UI thread, which possesses an independent OS thread, while UI-independent logic code can run on any OS thread. Since Cangjie code runs on Cangjie user-mode threads without explicit binding to OS threads, there is no guarantee that UI logic code will execute on the UI thread, potentially leading to application lag and security risks.

## Development Paradigm

Supports specifying code logic that can be custom-scheduled to run on either the UI thread or non-UI threads.

## Import Module

```cangjie
import kit.ArkUI.*
```

## let UIThread

```cangjie
public let UIThread: MainThreadContext = MainThreadContext.instance_
```

**Function:** UI thread context instance.

**Type:** MainThreadContext

**Read/Write Permission:** Read-only

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since Version:** 22

## func launch(() -> Unit)

```cangjie
public func launch(task: () -> Unit): Unit
```

**Function:** Submits a task to the main thread for execution.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since Version:** 22

**Parameters:**

| Parameter | Type       | Required | Default | Description          |
|:----------|:-----------|:---------|:--------|:---------------------|
| task      | () -> Unit | Yes      | -       | The task to execute. |

## class MainThreadContext

```cangjie
public class MainThreadContext <: ThreadContext {}
```

**Function:** Main thread context class.

**System Capability:** SystemCapability.ArkUI.ArkUI.Full

**Since Version:** 22

**Parent Type:**

- ThreadContext