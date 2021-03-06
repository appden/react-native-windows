# Event Tracing in ReactNative for Windows

React native for Windows implements an event provider using [Event Tracing for Windows (ETW)](https://docs.microsoft.com/en-us/windows/win32/etw/event-tracing-portal) framework, to enable instrumenting and analyzing performance critical source code. Events generated by an ETW provider can be observed and analyzed using tools available through [Windows Performance Toolkit (WPT)](https://docs.microsoft.com/en-us/windows-hardware/test/wpt/).

Currently, we have implemented the [Systrace APIs](https://stuff.mit.edu/afs/sipb/project/android/docs/tools/help/systrace.html) on Windows to generate ETW events. Systrace APIs are used to instrument the core React Native source code. In future, we will instrument more of the React Native Windows source code with ETW events.

Tracing sessions can be managed as described below,

## Start a tracing session

1. Trace only events generated by React Native For Windows providers,

```powershell
& .\vnext\Scripts\Tracing\Start-Tracing.ps1
```

2. Trace events generated by React Native For Windows as well as the general system providers,

```powershell
& .\vnext\Scripts\Tracing\Start-Tracing.ps1 -IncludeGeneralTrace=$True
```

## Stop a tracing session and anayze the traces

1. Stop the session and start anaylizing the traces,

```powershell
& .\vnext\Scripts\Tracing\Stop-Tracing.ps1
```

2. Stop the session only,

```powershell
& .\vnext\Scripts\Tracing\Stop-Tracing.ps1 -NoAnalysis=$True
```