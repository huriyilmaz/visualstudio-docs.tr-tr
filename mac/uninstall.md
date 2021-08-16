---
title: Kaldırma Mac için Visual Studio
description: Uygulamaları ve Mac için Visual Studio kaldırma yönergeleri.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.topic: how-to
ms.openlocfilehash: 6b781876861fb72634c5b22db655fd5905a962dd32b3028e6e10c382b8f8f8a8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121381628"
---
# <a name="uninstalling-visual-studio-for-mac"></a>Mac için Visual Studio kaldırılıyor

İlgili bölüme giderek bu kılavuzu kullanarak Mac için Visual Studio bileşenleri tek tek kaldırabilirsiniz veya Her şeyi kaldırmak için [](#uninstall-script) Betiği Kaldır bölümünde sağlanan betikleri kullanabilirsiniz.

> [!NOTE]
> Bu bilgiler yalnızca Mac için 2019 veya 2017 Visual Studio 2017'yi makineden kaldırır. yüklemesini Visual Studio Code için bu [soruna](https://github.com/Microsoft/vscode/issues/52151) bakın.

## <a name="uninstall-script"></a>Betiği Kaldırma

Makinenizin tüm bileşenlerini ve Mac için Visual Studio kaldırmak için 2 betik vardır:

- [Visual Studio ve Xamarin betiği](#visual-studio-for-mac-and-xamarin-script)
- [.NET Core betiği](#net-core-script)

Aşağıdaki bölümler betikleri indirme ve kullanma hakkında bilgi sağlar.

### <a name="visual-studio-for-mac-and-xamarin-script"></a>Mac için Visual Studio ve Xamarin betiği

Kaldırma betiği Visual Studio ve Xamarin bileşenlerini tek bir go'da [kaldırabilirsiniz.](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh)

Bu kaldırma betiği, makalede bulabilirsiniz komutlarının çoğunu içerir. Betikten üç ana eksiklik vardır ve olası dış bağımlılıklar nedeniyle dahil değildir. Bunu kaldırmak için aşağıdaki ilgili bölüme atlayın ve el ile kaldırın:

- **[Mono'ları kaldırma](#uninstall-mono-sdk-mdk)**
- **[Android AVD'sini kaldırma](#uninstall-android-avd)**
- **[Android SDK Ve Java SDK'sı kaldırma](#uninstall-android-sdk-and-java-sdk)**

Betiği çalıştırmak için aşağıdaki adımları uygulayın:

1. Betiği sağ tıklayın ve Dosyayı **Mac'inize** kaydetmek için Farklı Kaydet'i seçin.
2. Terminal'i açın ve çalışma dizinini betiğin indirilmiş olduğu dizin olarak değiştirme:

    ```bash
    cd /location/of/file
    ```

3. Betiği yürütülebilir hale çalıştırın ve **sudo ile çalıştırın:**

    ```bash
    chmod +x ./uninstall-vsmac.sh
    sudo ./uninstall-vsmac.sh
    ```

4. Son olarak kaldırma betiği silin ve Mac için Visual Studio (varsa) dock'tan kaldırın.

### <a name="net-core-script"></a>.NET Core betiği

.NET Core için kaldırma betiği [dotnet cli repo'sında bulunur](https://raw.githubusercontent.com/dotnet/cli/master/scripts/obtain/uninstall/dotnet-uninstall-pkgs.sh)

Betiği çalıştırmak için aşağıdaki adımları uygulayın:

1. Betiği sağ tıklayın ve Dosyayı **Mac'inize** kaydetmek için Farklı Kaydet'i seçin.
2. Terminal'i açın ve çalışma dizinini betiğin indirilmiş olduğu dizin olarak değiştirme:

    ```bash
    cd /location/of/file
    ```

3. Betiği yürütülebilir hale çalıştırın ve **sudo ile çalıştırın:**

    ```bash
    chmod +x ./dotnet-uninstall-pkgs.sh
    sudo ./dotnet-uninstall-pkgs.sh
    ```

4. Son olarak .NET Core kaldırma betiği silin.

## <a name="uninstall-visual-studio-for-mac"></a>Kaldırma Mac için Visual Studio

Mac'den Visual Studio kaldırmanın ilk **adımı, /Applications** dizininde **Visual Studio.app'i** bulup Çöp **Kutusu'na sürüklemektir.** Alternatif olarak, aşağıdaki görüntüde gösterildiği gibi **sağ tıklayın ve Çöp** Kutusuna Taşı'yı seçin:

![Uygulama Visual Studio çöp kutusuna taşıma](media/uninstall-image1.png)

Dosya sisteminde hala Xamarin Mac için Visual Studio başka dosyalar da olsa, bu uygulama paketi silinse bile bu uygulama paketi silindi.

Terminalde tüm Mac için Visual Studio kaldırmak için Terminal'de aşağıdaki komutları çalıştırın:

```bash
sudo rm -rf "/Applications/Visual Studio.app"
rm -rf ~/Library/Caches/VisualStudio
rm -rf ~/Library/Preferences/VisualStudio
rm -rf ~/Library/Preferences/Visual\ Studio
rm -rf ~/Library/Logs/VisualStudio
rm -rf ~/Library/VisualStudio
rm -rf ~/Library/Preferences/Xamarin/
rm -rf ~/Library/Application\ Support/VisualStudio
rm -rf ~/Library/Application\ Support/VisualStudio/7.0/LocalInstall/Addins/
rm -rf ~/Library/Application\ Support/VisualStudio/8.0/LocalInstall/Addins/
```

Ayrıca çeşitli Xamarin dosyalarını ve klasörlerini içeren aşağıdaki dizini kaldırmak da istiyor olabilir. Ancak, bunu yapmadan önce bu dizinin Android imzalama anahtarlarını içerdiğini fark edersiniz. Daha fazla bilgi için, Uygulamaları **[ve Java SDK Android SDK kaldırma bölümüne bakın:](#uninstall-android-sdk-and-java-sdk)**

```bash
rm -rf ~/Library/Developer/Xamarin
```

## <a name="uninstall-mono-sdk-mdk"></a>Mono SDK'yı (MDK) kaldırma

Mono, Microsoft'un .NET Framework'nin açık kaynak uygulamasıdır ve bu platformların C# ile geliştirilmesine izin vermek için Xamarin.iOS, Xamarin.Android ve Xamarin.Mac gibi tüm Xamarin Ürünleri tarafından kullanılır.

> [!WARNING]
> Uygulamanın dışında, Unity Mac için Visual Studio Mono kullanan başka uygulamalar da vardır.
> Kaldırmadan önce Mono'da başka bağımlılıklar olmadığını emin olun.

Mono Framework'leri bir makineden kaldırmak için Terminal'de aşağıdaki komutları çalıştırın:

```bash
sudo rm -rf /Library/Frameworks/Mono.framework
sudo pkgutil --forget com.xamarin.mono-MDK.pkg
sudo rm -rf /etc/paths.d/mono-commands
```

## <a name="uninstall-xamarinandroid"></a>Xamarin.Android'i kaldırma

Xamarin.Android'in yüklenmesi ve kullanımı için gerekli olan Android SDK Java SDK'sı gibi öğeler vardır.

Xamarin.Android'i kaldırmak için aşağıdaki komutları kullanın:

```bash
sudo rm -rf /Developer/MonoDroid
rm -rf ~/Library/MonoAndroid
sudo pkgutil --forget com.xamarin.android.pkg
sudo rm -rf /Library/Frameworks/Xamarin.Android.framework
```

### <a name="uninstall-android-sdk-and-java-sdk"></a>Android SDK ve Java SDK'sini kaldırma

Bu Android SDK Android uygulamalarının geliştirilmesi için gereklidir. Dosyanın tüm bölümlerini tamamen Android SDK için **~/Library/Developer/Xamarin/** içinde dosyasını bulun ve Çöp Kutusu'na **taşımanız gerekir.**

> [!WARNING]
> Uygulama tarafından oluşturulan Android imzalama anahtarlarının içinde olduğunu Mac için Visual Studio `~/Library/Developer/Xamarin/Keystore` gerekir. Bunları uygun şekilde destekleyenin veya anahtar deposu tutmak isterseniz bu dizini kaldırmaktan kaçının.

Java SDK'sı (JDK) zaten Mac OS X / macOS'un parçası olarak önceden paketlenmiştir.

### <a name="uninstall-android-avd"></a>Android AVD'sini kaldırma

> [!WARNING]
> Mac için Visual Studio dışında Android AVD ve Android Studio gibi bu ek Android bileşenlerini kullanan başka uygulamalar da vardır. Bu dizini kaldırmak projelerin verilerde hataya neden Android Studio.

Tüm Android AVD'leri ve ek Android bileşenlerini kaldırmak için aşağıdaki komutu kullanın:

```bash
rm -rf ~/.android
```

Yalnızca Android AVD'lerini kaldırmak için aşağıdaki komutu kullanın:

```bash
rm -rf ~/.android/avd
```

## <a name="uninstall-xamarinios"></a>Xamarin.iOS'u kaldırma

Xamarin.iOS, C# veya F# kullanarak iOS uygulama geliştirmeyi mümkün Mac için Visual Studio.

Bir dosya sisteminden tüm Xamarin.iOS dosyalarını kaldırmak için Terminal'de aşağıdaki komutları kullanın:

```bash
rm -rf ~/Library/MonoTouch
sudo rm -rf /Library/Frameworks/Xamarin.iOS.framework
sudo rm -rf /Developer/MonoTouch
sudo pkgutil --forget com.xamarin.monotouch.pkg
sudo pkgutil --forget com.xamarin.xamarin-ios-build-host.pkg
sudo pkgutil --forget com.xamarin.xamarin.ios.pkg
```

## <a name="uninstall-xamarinmac"></a>Xamarin.Mac'i kaldırma

Xamarin.Mac, sırasıyla Mac'inizin ürün ve lisansını ortadan kaldırmak için aşağıdaki iki komut kullanılarak makineden kaldırılabilir:

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>Çalışma Kitaplarını ve Denetçiyi Kaldırma

1.2.2'den başlayarak Xamarin Workbooks & Inspector şu çalıştırarak terminalden kaldırabilirsiniz:

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

Eski sürümler için aşağıdaki yapıtları el ile kaldırmanız gerekir:

* Çalışma kitapları uygulamasını şu sayfadan silin: `"/Applications/Xamarin Workbooks.app"`
* Denetçi uygulamasını şu sayfadan silin: `"Applications/Xamarin Inspector.app"`
* Eklentileri silin: `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` ve `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`
* Denetçiyi ve destek dosyalarını buradan silin: `/Library/Frameworks/Xamarin.Interactive.framework` ve `/Library/Frameworks/Xamarin.Inspector.framework`

## <a name="uninstall-the-xamarin-profiler"></a>Uninstall the Xamarin Profiler

```bash
sudo rm -rf "/Applications/Xamarin Profiler.app"
```

## <a name="uninstall-the-visual-studio-installer"></a>Visual Studio Yükleyicisi

Xamarin Evrensel Yükleyicisi'nin tüm izlemelerini kaldırmak için aşağıdaki komutları kullanın:

```bash
rm -rf ~/Library/Caches/XamarinInstaller/
rm -rf ~/Library/Caches/VisualStudioInstaller/
rm -rf ~/Library/Logs/XamarinInstaller/
rm -rf ~/Library/Logs/VisualStudioInstaller/
rm -rf ~/Library/Preferences/Xamarin/
rm -rf "~/Library/Preferences/Visual Studio/"
```

* * *

## <a name="uninstall-visual-studio-2019-for-mac-preview"></a>Mac Visual Studio 2019 Preview'ı kaldırma

mac Visual Studio 2019 önizlemesi ayrı bir önizleme olarak başlatılmıştı. Böylece, Mac için Visual Studio 2017'niz ile yan yana yüklemeyle çalışmaya devam edersiniz.

Mac için Visual Studio 2019 sürümü yayımlandı. Artık Mac için Visual Studio 2019 Önizleme uygulamasını güvenle kaldırabilirsiniz.

Önizleme uygulama paketi kaldırmak için, aşağıdaki görüntüde Visual Studio  Uygulamalar klasörünüzden Uygulama **(Önizleme)** öğesini seçin ve Çöp Kutusuna Taşı'ya tıklayın: 

![Bulıcıda "çöp kutusuna taşı" seçeneğini seçme](media/uninstall-remove-vspreview.png)

Aşağıdaki komutla Önizleme plist dosyasını da kaldırabilirsiniz:

```bash
rm -rf ~/Library/Preferences/com.microsoft.visual-studio-preview.plist
```

## <a name="see-also"></a>Ayrıca bkz.

- [Kaldırma Visual Studio (Windows)](/visualstudio/install/uninstall-visual-studio)
