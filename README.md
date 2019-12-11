# Ultralight

Ultralight is a lightweight, cross-platform, pure-GPU, HTML rendering engine for desktop apps and games. It supports most modern HTML5 and JavaScript features while still remaining small in binary size and memory usage.

API is currently available for C and C++, with bindings for more languages in development.

### Base Memory Usage

|            | Ultralight  | Electron  |
|------------|-------------|-----------|
| Windows    | 9 MB        | 72 MB     |
| macOS      | 17 MB       | 97 MB     |
| Linux      | 15 MB       | 136 MB    |

### Base Distributable Size

|            | Ultralight  | Electron  |
|------------|-------------|-----------|
| Windows    | 30 MB       | 147 MB    |
| macOS      | 43 MB       | 163 MB    |
| Linux      | 49 MB       | 179 MB    |

### Comparison with Chromium

|                   | Ultralight               | Chromium                    |
|-------------------|--------------------------|-----------------------------|
| Renderer          | Proprietary (GPU)        | Skia (CPU) / GPU Compositor |
| Layout Engine     | WebCore (from WebKit)    | Blink                       |
| JavaScript Engine | JavaScriptCore           | V8                          |
| IPC               | None (Single Process)    | Yes (Multi Process)         |

## Architecture

Ultralight is a new port of WebKit combined with a new 2D GPU renderer intended specifically for embedding in apps and games.

### Virtual GPU Renderer

The renderer emits virtual GPU commands that are translated into native GPU commands of the target platform at runtime. This approach makes it easy to embed Ultralight in games as well.

### Low-Level Platform API

Ultralight grants developers the ability to override low-level system calls for deeper integration with applications. We currently provide APIs to customize File System and Font Loading but will soon be expanding this to Clipboard, Memory Allocation, Network Requests, and more.

### Cross-Platform AppCore Runtime

AppCore is an optional, cross-platform desktop app runtime built on top of Ultralight that handles window creation, native event loops, native graphics drivers (D3D11, D3D12, Metal, OpenGL), and more.

You can use it to build desktop HTML apps in a manner similar to Electron. It's currently under active development and only supports single-window apps at this writing. A number of planned features (app icons, automatic packager, borderless windows with custom draggable titlebars, etc) are missing but on the way.

### Usage Within Games

Ultralight is designed to integrate well into existing game engines. In this case you would just use the low-level Ultralight API (not AppCore) and implement the GPUDriver interface for your target platform (we recommend using the drivers and shader code in the AppCore repo as a base).

## Licensing

Ultralight is _free_ for non-commercial use, and free for commercial use by small indies (<$100K annual revenue). For info regarding pricing/terms for larger commercial projects please email adam@ultralig.ht.

This project also uses LGPL code (the AppCore and WebCore modules)-- source is provided in adjacent repositories. You can use these modules in your code without being forced to release your code under LGPL as long as you A) link dynamically and B) release the source to any modifications you make.

## Getting the Latest SDK

You can get the latest SDK for each platform via the following links:

 * [Windows | x64 | Release](https://ultralight-sdk.sfo2.cdn.digitaloceanspaces.com/ultralight-sdk-latest-win-x64.7z)
 * [Windows | x86 | Release](https://ultralight-sdk.sfo2.cdn.digitaloceanspaces.com/ultralight-sdk-latest-win-x86.7z)
 * [Linux | x64 | Release](https://ultralight-sdk.sfo2.cdn.digitaloceanspaces.com/ultralight-sdk-latest-linux-x64.7z)
 * [macOS | x64 | Release](https://ultralight-sdk.sfo2.cdn.digitaloceanspaces.com/ultralight-sdk-latest-mac-x64.7z)

Debug packages are also available below:

 * [Windows | x64 | Debug](https://ultralight-sdk-dbg.sfo2.cdn.digitaloceanspaces.com/ultralight-sdk-latest-win-x64.7z)
 * [Windows | x86 | Debug](https://ultralight-sdk-dbg.sfo2.cdn.digitaloceanspaces.com/ultralight-sdk-latest-win-x86.7z)
 * [Linux | x64 | Debug](https://ultralight-sdk-dbg.sfo2.cdn.digitaloceanspaces.com/ultralight-sdk-latest-linux-x64.7z)
 * [macOS | x64 | Debug](https://ultralight-sdk-dbg.sfo2.cdn.digitaloceanspaces.com/ultralight-sdk-latest-mac-x64.7z)

 > *__Note__: Full debug symbols are only provided for WebCore and AppCore modules.*

### Getting Pre-Built Binaries for a Specific Commit

Pre-built binares are uploaded to the following S3 buckets every commit:

 * __Release Bins__: <https://ultralight-sdk.sfo2.cdn.digitaloceanspaces.com/>
 * __Debug Bins__: <https://ultralight-sdk-dbg.sfo2.cdn.digitaloceanspaces.com/>

Click any of the links for an XML listing of available files.

## Useful Links

| Link                       | URL                                                 |
| -------------------------- | --------------------------------------------------- |
| __Slack Channel__          | <https://chat.ultralig.ht>                          |
| __Twitter__                | <https://twitter.com/ultralight_ux>                 |
| __API Headers__            | <https://github.com/ultralight-ux/Ultralight-API/>  |
| __Docs / Getting Started__ | <https://docs.ultralig.ht>                          |

