# WiFi Mobile Configuration Profile Generator

## Recent Updates (2025-08-19)
- **Download機能の実装**: 「Copy to clipboard」ボタンを「Download」ボタンに変更し、生成されたプロファイルを直接ファイルとしてダウンロードできるようになりました
  - iOS: `.mobileconfig`ファイルとしてダウンロード
  - Android/Windows: `.xml`ファイルとしてダウンロード
- **clipboard.jsの削除**: ダウンロード機能への移行に伴い、clipboard.jsへの依存を削除しました
- **日本語化**: index.htmlとandroid.htmlのインターフェースを日本語に翻訳しました
  - ナビゲーション、説明文、フォームラベル、プレースホルダーテキストなどすべてのUI要素を日本語化
  - 技術的な参照リンクは元の言語のまま維持
- **動的UUID生成**: 複数のプロファイルをインストール可能にするため、UUIDを動的に生成する機能を追加
  - iOS: プロファイル内の3つのUUID（PayloadUUID、PayloadIdentifier）を入力変更時に自動生成
  - ファイル名にSSIDとタイムスタンプを含めることで、同じネットワークでも異なるプロファイルとして扱える
  - これにより、同じデバイスに複数の異なるWi-Fiプロファイルをインストール可能に

## Table of contents
  - [What does it do?](#what-does-it-do)
  - [How does it work?](#how-does-it-work)
  - [What frameworks are used?](#what-frameworks-are-used)
  - [How do I use it?](#how-do-i-use-it)
  - [Functions](#functions)
  - [Why?](#why)

## What does it do?

[Back to top](#table-of-contents)

When you manage your mobile devices (specifically, **iOS, Android or Windows devices**) via any source - an MDM, for example... this provider sends your device a *Configuration Profile* - this is the raw data that contain the information that they want to configure on your device. 

I've ran into a lot of scenarios where I need to make a Wi-Fi profile manually - troubleshooting, testing, or simply installing a standalone one without an MDM. 
On iOS, this is normally possible with a tool Apple provides called **Apple Configurator** - I do not have a Mac, and this tool only works on Mac devices - so this is the best next thing! 
Windows & Android use the same format, so you can typically export a configured Wi-Fi network from a Windows machine, and import into an MDM to deploy widespread, but also to your Android devices. 

This web app makes the job simple - you don't have to do any sort of exports, or use Apple Configurtor - you simply fill out the details, download the profile, and you can use it however you wish - the file is automatically saved in the correct format: ***wifi.mobileconfig*** for iOS, or ***wifi.xml*** for Windows & Android.

## How does it work?

[Back to top](#table-of-contents)

It's a standalone webpage (it does have CSS/JavaScript dependencies - more on this later). None of the information you provide ever leaves your browser. It reads the input that you provide into the fields, and replaces the corresponding fields in the generated profile.

## What frameworks are used?

[Back to top](#table-of-contents)

1. [Bootstrap](https://getbootstrap.com/) 4.4.1 for the CSS framework
2. [jQuery](https://jquery.com/) for the data validation / reading / manipulation 

Bootstrap and jQuery are loaded from their CDN.

## How do I use it?

[Back to top](#table-of-contents)

- You can simply use the GitHub pages link I have hosted! https://daduckmsft.github.io/WiFiProfileGenerator/
- Alternatively, you can download everything from [here](https://github.com/daduckMSFT/WiFiProfileGenerator/releases/latest), unzip, and enjoy! Nothing else needed - it should just work.
- If you want to host the dependencies yourself, you can surely do so, but it's way outside of the scope that I'll cover here!

## Functions

[Back to top](#table-of-contents)

I tried to document the functions in a manner that's fairly straightforward, but without some basic knowledge of Object Oriented Programming it might not be very clear. 
There is more information - you can see more info on them below.

- [Functions](https://github.com/daduckMSFT/WiFiProfileGenerator/wiki)

## Why?

[Back to top](#table-of-contents)

I made this because there used to be a website that allowed you to generate a custom / text-based Wi-Fi profile for iOS devices. 
Sadly, this no longer exists, and I've made this as it's spiritual successor! Johnathanb, if you're out there, I used your website a lot and was sad to see it was no longer there!