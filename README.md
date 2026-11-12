# sonmat-hook-wwise-wide

A part of 손맛 햅틱 / Sonmat Haptics (`sonmat`): dshaptics_wwise_wide.dll.

Hook for games with their own engine and Wwise (NieR:Automata): PostEvent by ID and SetRTPCValue found by byte patterns in sigs.txt beside the DLL (the game's own, put there by the app). With `SetPosition` (and `SetListenerPosition`, the pre-2017 listener API) patterns it also writes where the event's object is (`wpos:`) and where the listener is and faces (`wlis:`), only next to events.

The app does not carry this in its installer for good: it fetches the release zip that `sonmat-games/parts.json` names
(address + SHA-256) into `<app>/parts/hook-wwise-wide/` when a game needs it (`sonmat/tools/partfetch.py`). A change here reaches
players when a new tag has been released and `parts.json` points at it.

Build: Visual Studio C++ tools (x64), MinHook in minhook\ at the commit the workflow pins: build.bat dshaptics_wwise_wide. Every push to main builds it on GitHub (artifact); a tag `v*` makes the release.

MinHook (Tsuda Kageyu, BSD 2-Clause) is compiled in; its license is in the release zip as `MinHook-LICENSE.txt`.
