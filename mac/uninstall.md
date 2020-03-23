---
title: Mac için Visual Studio'u kaldır
description: Mac ve ilgili araçlar için Visual Studio'nun yüklenmesi için talimatlar.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.openlocfilehash: 348a6ad1bde58c17b2bbb1ef4868fcfa6835ef9f
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "76892174"
---
# <a name="uninstalling-visual-studio-for-mac"></a>Mac için Visual Studio kaldırılıyor

Bu kılavuzu, ilgili bölüme gezinerek Visual Studio for Mac'teki her bileşeni tek tek kaldırmak için veya Her Şeyi kaldırmak için [Komut Dosyasını Kaldır](#uninstall-script) bölümünde sağlanan komut dosyalarını kullanabilirsiniz.

> [!NOTE]
> Bu bilgiler, Mac için Visual Studio 2019 veya 2017'yi yalnızca makinenizden kaldırır. Visual Studio Code'u kaldırmak için ayrıntılar için [bu soruna](https://github.com/Microsoft/vscode/issues/52151) bakın.

## <a name="uninstall-script"></a>Komut Dosyalarını Kaldır

Mac için Visual Studio'yu kaldırmak için kullanılabilecek iki komut dosyası ve makinenizin tüm bileşenleri vardır:

- [Visual Studio ve Xamarin script](#visual-studio-for-mac-and-xamarin-script)
- [.NET Core komut dosyası](#net-core-script)

Aşağıdaki bölümlerde komut dosyalarının indirilmesi ve kullanılması hakkında bilgi verilmiştir.

### <a name="visual-studio-for-mac-and-xamarin-script"></a>Mac ve Xamarin komut dosyası için Visual Studio

Visual Studio ve Xamarin bileşenlerini tek bir noktada kaldır komut [dosyasını](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh)kullanarak kaldırabilirsiniz.

Bu kaldırma komutu, makalede bulabileceğiniz komutların çoğunu içerir. Komut dosyasından üç ana eksiklik vardır ve olası dış bağımlılıklar nedeniyle dahil edilmez. Bunu kaldırmak için aşağıdaki ilgili bölüme atlayın ve el ile kaldırın:

- **[Mono'nun Kaldırması](#uninstall-mono-sdk-mdk)**
- **[Android AVD'yi kaldırma](#uninstall-android-avd)**
- **[Android SDK ve Java SDK kaldırma](#uninstall-android-sdk-and-java-sdk)**

Komut dosyasını çalıştırmak için aşağıdaki adımları yapın:

1. Komut dosyasına sağ tıklayın ve dosyayı Mac'inize kaydetmek için **Kaydet'i** seçin.
2. Terminal'i açın ve çalışma dizini komut dosyasının indirildiği yer olarak değiştirin:

    ```bash
    cd /location/of/file
    ```

3. Komut dosyası çalıştırılabilir olun ve **sudo**ile çalıştırın:

    ```bash
    chmod +x ./uninstall-vsmac.sh
    sudo ./uninstall-vsmac.sh
    ```

4. Son olarak, kaldır komut dosyasını silin ve Mac için Visual Studio'yu dock'tan kaldırın (eğer oradaysa).

### <a name="net-core-script"></a>.NET Core komut dosyası

.NET Core için kaldırma komut dosyası [dotnet cli repo](https://raw.githubusercontent.com/dotnet/cli/master/scripts/obtain/uninstall/dotnet-uninstall-pkgs.sh) bulunur

Komut dosyasını çalıştırmak için aşağıdaki adımları yapın:

1. Komut dosyasına sağ tıklayın ve dosyayı Mac'inize kaydetmek için **Kaydet'i** seçin.
2. Terminal'i açın ve çalışma dizini komut dosyasının indirildiği yer olarak değiştirin:

    ```bash
    cd /location/of/file
    ```

3. Komut dosyası çalıştırılabilir olun ve **sudo**ile çalıştırın:

    ```bash
    chmod +x ./dotnet-uninstall-pkgs.sh
    sudo ./dotnet-uninstall-pkgs.sh
    ```

4. Son olarak, .NET Core kaldırma komut dosyasını silin.

## <a name="uninstall-visual-studio-for-mac"></a>Mac için Visual Studio'u kaldır

Visual Studio'yu Mac'ten kaldırmanın ilk adımı **Visual Studio.app'ı** **/Applications** dizininde bulmak ve **Çöp Kutusu'na**sürüklemektir. Alternatif olarak, aşağıdaki resimde gösterildiği gibi Sağa tıklayın ve **Çöp Kutusuna Taşı'nı** seçin:

![Visual Studio Uygulamasını çöpe taşı](media/uninstall-image1.png)

Bu uygulama paketini silerse, dosya sisteminde xamarin ile ilgili başka dosyalar olsa da, Mac için Visual Studio kaldırılır.

Mac için Visual Studio'nun tüm izlerini kaldırmak için Terminal'de aşağıdaki komutları çalıştırın:

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

Ayrıca, çeşitli Xamarin dosya ve klasörleri içeren aşağıdaki dizini kaldırmak isteyebilirsiniz. Ancak, bunu yapmadan önce bu dizinin Android imza anahtarlarını içerdiğini bilmeniz gerekir. Daha fazla bilgi için **[Android SDK ve Java SDK kaldırma](#uninstall-android-sdk-and-java-sdk)** bölümüne bakın:

```bash
rm -rf ~/Library/Developer/Xamarin
```

## <a name="uninstall-mono-sdk-mdk"></a>Mono SDK'yı Kaldır (MDK)

Mono, Microsoft'un .NET Framework'ünün açık kaynak uygulamasıdır ve c#'da bu platformların geliştirilmesine izin vermek için tüm Xamarin Ürünleri Xamarin.iOS, Xamarin.Android ve Xamarin.Mac tarafından kullanılmaktadır.

> [!WARNING]
> Visual Studio for Mac dışında Mono kullanan Unity gibi başka uygulamalar da vardır.
> Kaldırmadan önce Mono'ya başka bağımlılık olmadığından emin olun.

Mono Framework'u bir makineden kaldırmak için Terminal'de aşağıdaki komutları çalıştırın:

```bash
sudo rm -rf /Library/Frameworks/Mono.framework
sudo pkgutil --forget com.xamarin.mono-MDK.pkg
sudo rm -rf /etc/paths.d/mono-commands
```

## <a name="uninstall-xamarinandroid"></a>Xamarin.Android'i kaldırın

Android SDK ve Java SDK gibi Xamarin.Android'in kurulumu ve kullanımı için gerekli olan bir dizi öğe vardır.

Xamarin.Android kaldırmak için aşağıdaki komutları kullanın:

```bash
sudo rm -rf /Developer/MonoDroid
rm -rf ~/Library/MonoAndroid
sudo pkgutil --forget com.xamarin.android.pkg
sudo rm -rf /Library/Frameworks/Xamarin.Android.framework
```

### <a name="uninstall-android-sdk-and-java-sdk"></a>Android SDK ve Java SDK'yı kaldırın

Android SDK, Android uygulamalarının geliştirilmesi için gereklidir. Android SDK'nın tüm parçalarını tamamen kaldırmak için dosyayı **~/Library/Developer/Xamarin/** adresinde bulun ve **Çöp Kutusu'na**taşıyın.

> [!WARNING]
> Mac için Visual Studio tarafından oluşturulan Android imzalama anahtarlarının `~/Library/Developer/Xamarin/Keystore`. Bunları uygun şekilde yedeklediğinizden emin olun veya anahtar mağazanızı saklamak istiyorsanız bu dizini kaldırmaktan kaçının.

Zaten Mac OS X / macOS bir parçası olarak önceden paketlenmiş olduğu gibi Java SDK (JDK) kaldırılmalıdır gerekmez.

### <a name="uninstall-android-avd"></a>Android AVD'yi kaldırın

> [!WARNING]
> Ayrıca Android AVD ve android studio.Moving bu dizini kaldırma gibi bu ek android bileşenleri kullanmak Mac için Visual Studio dışında diğer uygulamalar vardır Projeler Android Studio kırmak için neden olabilir.

Android AVD'leri ve ek Android bileşenlerini kaldırmak için aşağıdaki komutu kullanın:

```bash
rm -rf ~/.android
```

Yalnızca Android AVD'leri kaldırmak için aşağıdaki komutu kullanın:

```bash
rm -rf ~/.android/avd
```

## <a name="uninstall-xamarinios"></a>Xamarin.iOS'u kaldırın

Xamarin.iOS, Mac için Visual Studio ile C# veya F# kullanarak iOS uygulama geliştirmesine olanak tanır.

Tüm Xamarin.iOS dosyalarını bir dosya sisteminden kaldırmak için Terminal'deki aşağıdaki komutları kullanın:

```bash
rm -rf ~/Library/MonoTouch
sudo rm -rf /Library/Frameworks/Xamarin.iOS.framework
sudo rm -rf /Developer/MonoTouch
sudo pkgutil --forget com.xamarin.monotouch.pkg
sudo pkgutil --forget com.xamarin.xamarin-ios-build-host.pkg
sudo pkgutil --forget com.xamarin.xamarin.ios.pkg
```

## <a name="uninstall-xamarinmac"></a>Xamarin.Mac'i kaldır

Xamarin.Mac, mac'inizden sırasıyla ürün ve lisansı ortadan kaldırmak için aşağıdaki iki komutu kullanarak makinenizden kaldırılabilir:

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>Çalışma Defterlerini ve Denetçiyi Kaldır

1.2.2 ile başlayarak, Xamarin Çalışma Kitapları & Denetçi çalıştırılarak bir terminalden kaldırılabilir:

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

Eski sürümler için aşağıdaki yapıları el ile kaldırmanız gerekir:

* Çalışma Kitapları uygulamasını silme`"/Applications/Xamarin Workbooks.app"`
* Müfettiş uygulamasını şu anda silme`"Applications/Xamarin Inspector.app"`
* Eklentileri silin: `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` ve`"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`
* Denetçi'yi ve destekleyici `/Library/Frameworks/Xamarin.Interactive.framework` dosyaları burada silin: ve`/Library/Frameworks/Xamarin.Inspector.framework`

## <a name="uninstall-the-xamarin-profiler"></a>Xamarin Profiloluşturun'u kaldırın

```bash
sudo rm -rf "/Applications/Xamarin Profiler.app"
```

## <a name="uninstall-the-visual-studio-installer"></a>Visual Studio Yükleyicisini Kaldırın

Xamarin Universal Installer'ın tüm izlerini kaldırmak için aşağıdaki komutları kullanın:

```bash
rm -rf ~/Library/Caches/XamarinInstaller/
rm -rf ~/Library/Caches/VisualStudioInstaller/
rm -rf ~/Library/Logs/XamarinInstaller/
rm -rf ~/Library/Logs/VisualStudioInstaller/
rm -rf ~/Library/Preferences/Xamarin/
rm -rf "~/Library/Preferences/Visual Studio/"
```

* * * 





## <a name="uninstall-visual-studio-2019-for-mac-preview"></a>Mac Önizleme için Visual Studio 2019'u kaldır

Mac Önizleme için Visual Studio 2019 ayrı bir önizleme olarak başlatıldı ve Mac'i yan yana yüklemek için Visual Studio 2017 ile çalışmaya devam edebilirsiniz.

Mac için Visual Studio 2019 piyasaya sürüldüğe göre, Mac Preview uygulaması için Visual Studio 2019'u güvenli bir şekilde kaldırabilirsiniz.

Önizleme uygulama paketini kaldırmak için **Uygulamalar** klasörünüzden **Visual Studio 'yu (Önizleme)** seçin ve aşağıdaki resimde belirtildiği gibi **Çöp Kutusuna Taşı'nı**tıklatın:

![bulucuda "çöp kutusuna taşı" seçeneğini seçme](media/uninstall-remove-vspreview.png)

Önizleme plist dosyasını aşağıdaki komutla da kaldırabilirsiniz:

```bash
rm -rf ~/Library/Preferences/com.microsoft.visual-studio-preview.plist
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'u kaldır (Windows'da)](/visualstudio/install/uninstall-visual-studio)