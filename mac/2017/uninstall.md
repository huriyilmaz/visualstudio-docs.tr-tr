---
title: Mac için Visual Studio kaldır
description: Mac için Visual Studio ve ilgili araçları kaldırmaya yönelik yönergeler.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.openlocfilehash: ad0be8546b88fbd01f54faf7eb00f71ddd6aa632
ms.sourcegitcommit: 6375001ab26786af8d4d449f5846f8a49779ed18
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2020
ms.locfileid: "76892161"
---
# <a name="uninstalling-visual-studio-for-mac"></a>Mac için Visual Studio kaldırılıyor

Mac için Visual Studio gibi tek başına uygulamalar dahil olmak üzere platformlar arası uygulama geliştirmeyi etkinleştiren birçok Xamarin ürünü vardır.

İlgili bölüme giderek her bir ürünü tek tek kaldırmak için bu Kılavuzu kullanabilirsiniz veya [kaldırma betiği](#uninstall-script) bölümünde sunulan betikleri kullanarak her şeyi kaldırabilirsiniz.

## <a name="uninstall-script"></a>Betiği kaldır

Makinenize yönelik Mac için Visual Studio ve tüm bileşenleri kaldırmak için kullanılabilecek iki betik vardır:

- [Visual Studio ve Xamarin betiği](#visual-studio-for-mac-and-xamarin-script)
- [.NET Core betiği](#net-core-script)

Aşağıdaki bölümler, betikleri indirme ve kullanmayla ilgili bilgiler sağlar.

### <a name="visual-studio-for-mac-and-xamarin-script"></a>Mac için Visual Studio ve Xamarin betiği

[Kaldırma betiğini](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh)kullanarak Visual Studio ve Xamarin bileşenlerini tek bir şekilde kaldırabilirsiniz.

Bu kaldırma betiği, makalede bulacağınız komutların çoğunu içerir. Betikten üç ana izin vardır ve olası dış bağımlılıklar nedeniyle dahil değildir. Bunu kaldırmak için aşağıdaki ilgili bölüme atlayın ve bunları el ile kaldırın:

- **[Mono kaldırılıyor](#uninstall-mono-sdk-mdk)**
- **[Android AVD 'yi kaldırma](#uninstall-android-avd)**
- **[Android SDK ve Java SDK 'sını kaldırma](#uninstall-android-sdk-and-java-sdk)**

Betiği çalıştırmak için aşağıdaki adımları uygulayın:

1. Dosyayı Mac 'e kaydetmek için komut dosyasına sağ tıklayın ve **farklı kaydet** ' i seçin.
2. Terminali açın ve çalışma dizinini betiğin indirildiği yere değiştirin:

    ```bash
    cd /location/of/file
    ```

3. Betiği çalıştırılabilir yapın ve **sudo**ile çalıştırın:

    ```bash
    chmod +x ./uninstall-vsmac.sh
    sudo ./uninstall-vsmac.sh
    ```

4. Son olarak, kaldırma betiğini silin.

### <a name="net-core-script"></a>.NET Core betiği

.NET Core için kaldırma betiği [DotNet CLI](https://raw.githubusercontent.com/dotnet/cli/master/scripts/obtain/uninstall/dotnet-uninstall-pkgs.sh) deposunda bulunur

Betiği çalıştırmak için aşağıdaki adımları uygulayın:

1. Dosyayı Mac 'e kaydetmek için komut dosyasına sağ tıklayın ve **farklı kaydet** ' i seçin.
2. Terminali açın ve çalışma dizinini betiğin indirildiği yere değiştirin:

    ```bash
    cd /location/of/file
    ```

3. Betiği çalıştırılabilir yapın ve **sudo**ile çalıştırın:

    ```bash
    chmod +x ./dotnet-uninstall-pkgs.sh
    sudo ./dotnet-uninstall-pkgs.sh
    ```

4. Son olarak, .NET Core kaldırma betiğini silin.

## <a name="uninstall-visual-studio-for-mac"></a>Mac için Visual Studio kaldır

Bir Mac 'ten Visual Studio 'Yu kaldırmanın ilk adımı, **/Apps** dizinindeki **Visual Studio. app** ' i bullemektir ve **çöp kutusuna**sürüklemektir. Alternatif olarak, sağ tıklayın ve aşağıdaki görüntüde gösterildiği gibi **çöp kutusuna taşı** ' yı seçin:

![Visual Studio uygulamasını çöp kutusuna taşıma](media/uninstall-image1.png)

Bu uygulama paketinin silinmesi, Xamarin ile ilgili başka dosyalar da dosya sisteminde hala mevcut olsa bile Mac için Visual Studio kaldırır.

Tüm Mac için Visual Studio izlemelerini kaldırmak için terminalde aşağıdaki komutları çalıştırın:

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
```

Ayrıca, çeşitli Xamarin dosyalarını ve klasörlerini içeren aşağıdaki dizini kaldırmak isteyebilirsiniz. Ancak, bunu yapmadan önce bu dizinin Android imzalama anahtarlarını içerdiğini bilmeniz gerekir. Daha fazla bilgi için **[Android SDK ve Java SDK 'Sını kaldırma](#uninstall-android-sdk-and-java-sdk)** bölümüne bakın:

```bash
rm -rf ~/Library/Developer/Xamarin
```

## <a name="uninstall-mono-sdk-mdk"></a>Mono SDK 'sını Kaldır (MDK)

Mono, Microsoft 'un .NET Framework açık kaynaklı bir uygulamasıdır ve ' de C#bu platformların geliştirilmesine izin vermek için Xamarin. IOS, Xamarin. Android ve Xamarin. Mac tüm Xamarin ürünleri tarafından kullanılır.

> [!WARNING]
> Mac için Visual Studio dışında, Unity gibi mono kullanan başka uygulamalar da vardır.
> Kaldırmadan önce mono üzerinde başka bağımlılıklar olmadığından emin olun.

Mono çerçevesini bir makineden kaldırmak için terminalde aşağıdaki komutları çalıştırın:

```bash
sudo rm -rf /Library/Frameworks/Mono.framework
sudo pkgutil --forget com.xamarin.mono-MDK.pkg
sudo rm -rf /etc/paths.d/mono-commands
```

## <a name="uninstall-xamarinandroid"></a>Xamarin. Android 'i kaldır

Android SDK ve Java SDK gibi Xamarin. Android ' in yüklenmesi ve kullanılması için gereken sayıda öğe vardır.

Xamarin. Android ' i kaldırmak için aşağıdaki komutları kullanın:

```bash
sudo rm -rf /Developer/MonoDroid
rm -rf ~/Library/MonoAndroid
sudo pkgutil --forget com.xamarin.android.pkg
sudo rm -rf /Library/Frameworks/Xamarin.Android.framework
```

### <a name="uninstall-android-sdk-and-java-sdk"></a>Android SDK ve Java SDK 'sını kaldırma

Android uygulamalarının geliştirilmesi için Android SDK gereklidir. Android SDK tüm parçalarını tamamen kaldırmak için, dosyayı **~/Library/Developer/Xamarin/** adresinde bulun ve **çöp kutusuna**taşıyın.

> [!WARNING]
> Mac için Visual Studio tarafından oluşturulan Android imzalama anahtarlarının `~/Library/Developer/Xamarin/Keystore`yer aldığını unutmayın. Bunları uygun şekilde yedeklediğinizden emin olun veya keystore 'u tutmak istiyorsanız bu dizini kaldırmaktan kaçının.

Java SDK (JDK) Mac OS X/macOS 'un bir parçası olarak önceden paketlendiğinden kaldırılması gerekmez.

### <a name="uninstall-android-avd"></a>Android AVD 'yi kaldır

> [!WARNING]
> Mac için Visual Studio dışında, Android AVD ve Android Studio gibi bu ek Android bileşenleri de kullanan başka uygulamalar vardır. bu dizini kaldırmak, projelerin Android Studio kesintiye neden olabilir.

Android AVDs ve ek Android bileşenleri kaldırmak için aşağıdaki komutu kullanın:

```bash
rm -rf ~/.android
```

Yalnızca Android AVDs 'yi kaldırmak için aşağıdaki komutu kullanın:

```bash
rm -rf ~/.android/avd
```

## <a name="uninstall-xamarinios"></a>Xamarin. iOS 'ı kaldır

Xamarin. iOS Mac için Visual Studio kullanarak C# veya F# ile iOS uygulama geliştirmeye olanak sağlar.

Tüm Xamarin. iOS dosyalarını bir dosya sisteminden kaldırmak için terminalde aşağıdaki komutları kullanın:

```bash
rm -rf ~/Library/MonoTouch
sudo rm -rf /Library/Frameworks/Xamarin.iOS.framework
sudo rm -rf /Developer/MonoTouch
sudo pkgutil --forget com.xamarin.monotouch.pkg
sudo pkgutil --forget com.xamarin.xamarin-ios-build-host.pkg
sudo pkgutil --forget com.xamarin.xamarin.ios.pkg
```

## <a name="uninstall-xamarinmac"></a>Xamarin. Mac 'i kaldır

Xamarin. Mac, aşağıdaki iki komut kullanılarak makinenizden kaldırılabilir ve bu şekilde Mac 'Inizden ürün ve lisans sağlayabilirsiniz:

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>Çalışma kitaplarını ve Inspector 'ı kaldırma

1\.2.2 ile başlayarak, Xamarin Workbooks & denetçisi çalıştırılarak bir terminalden kaldırılabilir:

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

Eski sürümler için aşağıdaki yapıtları el ile kaldırmanız gerekir:

* `"/Applications/Xamarin Workbooks.app"` çalışma kitapları uygulamasını silme
* `"Applications/Xamarin Inspector.app"` 'de Inspector uygulamasını silme
* Eklentileri silme: `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` ve `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`
* Inspector ve destekleyici dosyaları şurada Sil: `/Library/Frameworks/Xamarin.Interactive.framework` ve `/Library/Frameworks/Xamarin.Inspector.framework`

## <a name="uninstall-the-xamarin-profiler"></a>Xamarin Profiler kaldırın

```bash
sudo rm -rf "/Applications/Xamarin Profiler.app"
```

## <a name="uninstall-the-visual-studio-installer"></a>Visual Studio Yükleyicisi kaldırın

Xamarin Universal yükleyicisinin tüm izlemelerini kaldırmak için aşağıdaki komutları kullanın:

```bash
rm -rf ~/Library/Caches/XamarinInstaller/
rm -rf ~/Library/Caches/VisualStudioInstaller/
rm -rf ~/Library/Logs/XamarinInstaller/
rm -rf ~/Library/Logs/VisualStudioInstaller/
rm -rf ~/Library/Preferences/Xamarin/
rm -rf "~/Library/Preferences/Visual Studio/"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'Yu Kaldır (Windows üzerinde)](/visualstudio/install/uninstall-visual-studio)