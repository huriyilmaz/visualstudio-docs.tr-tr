---
title: Mac için Visual Studio kaldır
description: Mac için Visual Studio ve ilgili araçları kaldırın.
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 09/18/2019
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.topic: how-to
ms.openlocfilehash: 9e140a570a03dd34113d9b81eb536b9419519f11
ms.sourcegitcommit: 782992423db6e1cbbf206715c9b3b400c80052a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2022
ms.locfileid: "138101100"
---
# <a name="uninstall-visual-studio-for-mac"></a>Mac için Visual Studio kaldır 

ilgili bölüme giderek Mac için Visual Studio her bileşeni tek tek kaldırmak için bu kılavuzu kullanabilirsiniz veya [kaldırma betiği](#uninstall-script) bölümünde sunulan betikleri kullanarak her şeyi kaldırabilirsiniz.

Bu makale Visual Studio yöneliktir. VS Code hakkında bilgi arıyorsanız, bkz. [Visual Studio Code kurulum](https://code.visualstudio.com/docs/setup/setup-overview).

> [!NOTE]
> Mac için Visual Studio neden kaldırdığımızda daha fazla bilgi edinmek istiyoruz. bu sayede daha iyi hale getirebiliriz. Birkaç dakikanız varsa [lütfen geri bildiriminizi paylaşabilirsiniz](https://aka.ms/vs/mac/uninstallsurvey). Teşekkür ederiz!


## <a name="uninstall-script"></a>Betiği kaldır

makinenize yönelik Mac için Visual Studio ve tüm bileşenleri kaldırmak için kullanılabilecek iki betik vardır:

- [Visual Studio ve Xamarin betiği](#visual-studio-for-mac-and-xamarin-script)
- [.NET Core betiği](#net-core-script)

Aşağıdaki bölümler, betikleri indirme ve kullanmayla ilgili bilgiler sağlar.

### <a name="visual-studio-for-mac-and-xamarin-script"></a>Mac için Visual Studio ve Xamarin betiği

[kaldırma betiğini](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh)kullanarak Visual Studio ve Xamarin bileşenlerini tek bir şekilde kaldırabilirsiniz.

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

3. Betiği çalıştırılabilir yapın ve **sudo** ile çalıştırın:

    ```bash
    chmod +x ./uninstall-vsmac.sh
    sudo ./uninstall-vsmac.sh
    ```

4. son olarak, kaldırma betiğini silin ve Mac için Visual Studio dock 'tan kaldırın (varsa).

### <a name="net-core-script"></a>.NET Core betiği

.NET Core için kaldırma betiği [DotNet CLI](https://raw.githubusercontent.com/dotnet/cli/master/scripts/obtain/uninstall/dotnet-uninstall-pkgs.sh) deposunda bulunur

Betiği çalıştırmak için aşağıdaki adımları uygulayın:

1. Dosyayı Mac 'e kaydetmek için komut dosyasına sağ tıklayın ve **farklı kaydet** ' i seçin.
2. Terminali açın ve çalışma dizinini betiğin indirildiği yere değiştirin:

    ```bash
    cd /location/of/file
    ```

3. Betiği çalıştırılabilir yapın ve **sudo** ile çalıştırın:

    ```bash
    chmod +x ./dotnet-uninstall-pkgs.sh
    sudo ./dotnet-uninstall-pkgs.sh
    ```

4. Son olarak, .NET Core kaldırma betiğini silin.

## <a name="uninstall-visual-studio-for-mac"></a>Mac için Visual Studio kaldır

Mac 'ten Visual Studio kaldırmanın ilk adımı, **/apps** dizinindeki **Visual Studio. app** ' i bullemektir ve **çöp kutusu**' na sürüklemektir. Alternatif olarak, sağ tıklayın ve aşağıdaki görüntüde gösterildiği gibi **çöp kutusuna taşı** ' yı seçin:

![Visual Studio uygulamayı çöp kutusuna taşıma](media/uninstall-image1.png)

bu uygulama paketinin silinmesi, Xamarin ile ilgili başka dosyalar da dosya sisteminde hala mevcut olsa bile Mac için Visual Studio kaldırır.

tüm Mac için Visual Studio izlemelerini kaldırmak için terminalde aşağıdaki komutları çalıştırın:

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

Ayrıca, çeşitli Xamarin dosyalarını ve klasörlerini içeren aşağıdaki dizini kaldırmak isteyebilirsiniz. Ancak, bunu yapmadan önce bu dizinin Android imzalama anahtarlarını içerdiğini bilmeniz gerekir. Daha fazla bilgi için **[Android SDK ve Java SDK 'Sını kaldırma](#uninstall-android-sdk-and-java-sdk)** bölümüne bakın:

```bash
rm -rf ~/Library/Developer/Xamarin
```

## <a name="uninstall-mono-sdk-mdk"></a>Mono SDK 'sını Kaldır (MDK)

Mono, Microsoft 'un .NET Framework açık kaynaklı bir uygulamasıdır ve C# dilinde bu platformların geliştirilmesine izin vermek için xamarin. iOS, xamarin. Android ve xamarin. Mac tüm xamarin ürünleri tarafından kullanılır.

> [!WARNING]
> Mac için Visual Studio dışında, Unity gibi Mono kullanan başka uygulamalar da vardır.
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

Android uygulamalarının geliştirilmesi için Android SDK gereklidir. Android SDK tüm parçalarını tamamen kaldırmak için, dosyayı **~/Library/Developer/Xamarin/** adresinde bulun ve **çöp kutusuna** taşıyın.

> [!WARNING]
> Mac için Visual Studio tarafından oluşturulan Android imzalama anahtarlarının içinde `~/Library/Developer/Xamarin/Keystore` bulunduğunu bilmelisiniz. Bunları uygun şekilde yedeklediğinizden emin olun veya keystore 'u tutmak istiyorsanız bu dizini kaldırmaktan kaçının.

Java SDK (JDK) Mac OS X/macOS 'un bir parçası olarak önceden paketlendiğinden kaldırılması gerekmez.

### <a name="uninstall-android-avd"></a>Android AVD 'yi kaldır

> [!WARNING]
> Mac için Visual Studio dışında, android avd ve Android Studio gibi bu ek android bileşenleri de kullanan başka uygulamalar vardır. bu dizini kaldırmak, projelerin Android Studio kesintiye neden olabilir.

Android AVDs ve ek Android bileşenleri kaldırmak için aşağıdaki komutu kullanın:

```bash
rm -rf ~/.android
```

Yalnızca Android AVDs 'yi kaldırmak için aşağıdaki komutu kullanın:

```bash
rm -rf ~/.android/avd
```

## <a name="uninstall-xamarinios"></a>Xamarin. iOS 'ı kaldır

Xamarin. ios, Mac için Visual Studio ile C# veya F # kullanarak iOS uygulama geliştirmeye olanak sağlar.

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

1.2.2 ile başlayarak, Xamarin Workbooks & denetçisi çalıştırılarak bir terminalden kaldırılabilir:

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

Eski sürümler için aşağıdaki yapıtları el ile kaldırmanız gerekir:

* Çalışma kitapları uygulamasını şurada silin: `"/Applications/Xamarin Workbooks.app"`
* Inspector uygulamasını şurada Sil: `"Applications/Xamarin Inspector.app"`
* Eklentileri silin: `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` ve `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`
* Inspector ve destekleyici dosyaları şurada silin: `/Library/Frameworks/Xamarin.Interactive.framework` ve `/Library/Frameworks/Xamarin.Inspector.framework`

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

* * *

## <a name="uninstall-visual-studio-2019-for-mac-preview"></a>Mac önizlemesi için Visual Studio 2019 'yi kaldırın

mac önizlemesi için Visual Studio 2019, ayrı bir önizleme olarak başlatıldığından, mac için Visual Studio 2017 ' i yan yana yüklemeye devam edebilmenizi sağlar.

mac için Visual Studio 2019 artık yayımlandığına göre artık mac için Visual Studio 2019 önizleme uygulamasını güvenle kaldırabilirsiniz.

önizleme uygulaması paketini kaldırmak için, **uygulamalar** klasörünüzdeki **Visual Studio (önizleme)** öğesini seçin ve aşağıdaki görüntüde gösterildiği gibi **çöp kutusuna taşı**' ya tıklayın:

![Finder 'da "çöp kutusuna taşı" seçeneği seçiliyor](media/uninstall-remove-vspreview.png)

Önizleme plist dosyasını aşağıdaki komutla de kaldırabilirsiniz:

```bash
rm -rf ~/Library/Preferences/com.microsoft.visual-studio-preview.plist
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio kaldır (Windows)](/visualstudio/install/uninstall-visual-studio)
- [Visual Studio Code kaldır](https://github.com/Microsoft/vscode/issues/52151)
