# tOS

tOS-Lite is an ultra-lightweight, high-speed embedded CLI multi-user development platform based on Debian 13, capable of displaying a console screen on the Raspberry Pi 5 (ARM64) in approximately two seconds. By minimizing unnecessary background services and virtual graphics processing, it consumes less than 200 MB of memory and 900 MB of storage upon booting, allowing the majority of system resources to be dedicated to development tasks.

It integrates `uv` into the system core to systematically manage Python runtimes and packages. This approach ensures the stability of the base system environment while flexibly providing isolated environments for individual users.

The default shell is based on Zsh, configured with the Oh-My-Zsh plugin framework and the Powerlevel10k prompt engine; additionally, modern Rust- and Go-based CLI tools are pre-mapped as global aliases for standard Unix commands (such as `ls`, `cat`, `grep`, `top`, and `df`).

Based on tOS-Lite, tOS-Lite AI comes pre-configured with components essential for vision AI inference—such as OpenCV, PyTorch (torch, torchvision), ONNX, ONNX Runtime, and Netron—and occupies approximately 1.8 GB of storage space.

[tOS-Lite AI Last Image](https://github.com/PlanXLab/tOS/releases/latest/download/tOS-Lite-Ai.img.xz)
