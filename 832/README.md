# Issue #678: Windows taskbar progress

Before: upstream 05d92703. After: the same source with the reviewed #678 fix. Actual Windows 11 Pro build 26300 taskbar pixels, cropped to the test buttons and enlarged 3x; labels were added outside the crops. Two generated loopback downloads are near 25% and 50%, with a main aggregate near 37.5%.

Temporary per-window AppUserModelIDs expose each test window's button. This is test setup only: the fix does not force separate buttons or change system grouping preferences. When Windows combines buttons, it chooses the group indicator; that visible value can differ from the main window's aggregate.

appearance-languages.png covers before/after with light/dark app settings and English, German and Arabic. The changed surface is Windows' taskbar indicator, not the app's drawn controls. Windows' own taskbar appearance stays the same across app themes/languages; system preferences were not changed. Filenames and test content are neutral, and unrelated desktop content was cropped out.

Pause, cancellation, error and completion clear indicators; closing a progress window leaves its transfer and the main aggregate running. Those cleanup paths were checked in the app and six focused regressions. There are no new interface strings.

Windows 10 and mixed-monitor system DPI were not tested. The earlier 125% check uses app interface size.
