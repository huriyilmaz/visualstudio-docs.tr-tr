---
title: Yükleme sorunlarını giderme veya yükseltme sorunları
description: Bazı durumlarda sorunlar. Visual Studio yüklemesi veya yükseltmesi başarısız olursa, bu sayfa yardımcı olabilir.
ms.date: 09/13/2019
ms.custom: seodec18
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9dfdf504378dafd7d71288cae1927dd8d6bb9e56
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115003"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Visual Studio yükleme ve yükseltme sorunlarını giderme

> [!IMPORTANT]
> Yükleme sorun yaşıyorsunuz? Size yardımcı olabiliriz. Sunuyoruz bir [ **canlı sohbet** ](https://visualstudio.microsoft.com/vs/support/#talktous) (yalnızca İngilizce) destek seçeneği.

Bu sorun giderme kılavuzu çoğu yükleme sorunları çözmelisiniz adım adım yönergeler içerir.

## <a name="online-installations"></a>Çevrimiçi Yüklemeler

Aşağıdaki adımları, tipik bir çevrimiçi yükleme için en iyi duruma getirilir. Çevrimdışı yükleme etkileyen bir sorun için lütfen bkz [çevrimdışı yükleme sorunlarını giderme](#offline-installations).

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>1\. adım - bu sorunun bilinen bir sorun olup olmadığını denetleyin

::: moniker range="vs-2017"

Microsoft düzeltmek için çalışmaktadır Visual Studio Yükleyicisi ile ilgili bazı bilinen sorunlar vardır. Sorununuz için geçici bir çözüm olup olmadığını görmek için [sürüm notlarımızda bilinen sorunlar bölümünü](/visualstudio/releasenotes/vs2017-relnotes#-known-issues).

::: moniker-end

::: moniker range="vs-2019"

Microsoft düzeltmek için çalışmaktadır Visual Studio Yükleyicisi ile ilgili bazı bilinen sorunlar vardır. Sorununuz için geçici bir çözüm olup olmadığını görmek için [sürüm notlarımızda bilinen sorunlar bölümünü](/visualstudio/releases/2019/release-notes#-known-issues).

::: moniker-end

### <a name="step-2---check-with-the-developer-community"></a>Adım 2 - Geliştirici topluluğu denetimiyle

Arama, hata iletisiyle [Visual Studio Geliştirici topluluğu](https://developercommunity.visualstudio.com/spaces/8/index.html). Diğer topluluk üyelerinin belgelenmiş bir çözüm.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>3\. adım - yükseltme sorunlarını gidermek için Visual Studio yükleyicisi dizinini Sil

Visual Studio yükleyicisi önyükleyici, Visual Studio Yükleyicisi'nin rest yükleyen en az bir hafif çalıştırılabilir öğesidir. Bazı güncelleştirme hataları, Visual Studio Installer dosyalarını silerek ve sonra önyükleyici artırarak algoritmanın yeniden çalıştırılması çözebilir.

> [!NOTE]
> Aşağıdaki eylemleri gerçekleştirerek, Visual Studio Installer dosyalarını yükler ve yükleme meta verileri sıfırlar.

::: moniker range="vs-2017"

1. Visual Studio Yükleyicisi’ni kapatın.
2. Visual Studio yükleyicisi dizini silin. Genellikle, dizindir `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Visual Studio yükleyicisi önyükleyici çalıştırın. İndirmeler klasörüne bir dosya adıyla izleyen önyükleyici bulabileceğiniz bir `vs_[Visual Studio edition]__*.exe` deseni. Bu uygulamayı bulamazsanız, önyükleyici giderek indirebilirsiniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfası ve tıklayarak **indirme** Visual Studio sürümünüz için. Ardından yükleme meta verilerinizi sıfırlamak için yürütülebilir dosyayı çalıştırın.
4. Yükleme veya Visual Studio güncelleştirmeyi yeniden deneyin. Yükleyici başarısız olmaya devam ederse, sonraki adıma gidin.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio Yükleyicisi’ni kapatın.
2. Visual Studio yükleyicisi dizini silin. Genellikle, dizindir `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Visual Studio yükleyicisi önyükleyici çalıştırın. İndirmeler klasörüne bir dosya adıyla izleyen önyükleyici bulabileceğiniz bir `vs_[Visual Studio edition]__*.exe` deseni. Bu uygulamayı bulamazsanız, önyükleyici giderek indirebilirsiniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfası ve tıklayarak **indirme** Visual Studio sürümünüz için. Ardından yükleme meta verilerinizi sıfırlamak için yürütülebilir dosyayı çalıştırın.
4. Yükleme veya Visual Studio güncelleştirmeyi yeniden deneyin. Yükleyici başarısız olmaya devam ederse, sonraki adıma gidin.

::: moniker-end

### <a name="step-4---report-a-problem"></a>4\. adım - sorun bildirin

Bozuk dosyalarla ilgili olanlar gibi bazı durumlarda olay olarak denetlenmesi sırasında sorunlar yaşayabilirsiniz. Yardımımıza katkıda yardımcı olmak için lütfen aşağıdakileri yapın:

::: moniker range="vs-2017"

1. Uygulamanızın Kurulum günlükleri toplayın. Bkz: [Visual Studio yükleme günlüklerini almak nasıl](#installation-logs) Ayrıntılar için.
2. Visual Studio Yükleyicisi'ni açın ve ardından **sorun bildir** Visual Studio geri bildirim aracını açın.
![Geri bildirim aracını açmak için geri bildirim sağlamak düğmesine sekme](media/report-a-problem.png)
3. Sorun raporunuza bir başlık verin ve ilgili ayrıntıları sağlayın. Tıklayın **sonraki** gitmek için **ekleri** bölümüne ve ardından oluşturulan günlük dosyasını ekleyin (dosya altındadır genellikle `%TEMP%\vslogs.zip`).
4. Tıklayın **sonraki** sorun raporunuzu gözden geçirin ve ardından **Gönder**.

::: moniker-end

::: moniker range="vs-2019"

1. Uygulamanızın Kurulum günlükleri toplayın. Bkz: [Visual Studio yükleme günlüklerini almak nasıl](#installation-logs) Ayrıntılar için.
2. Visual Studio Yükleyicisi'ni açın ve ardından **sorun bildir** Visual Studio geri bildirim aracını açın.
![Geri bildirim aracını açmak için geri bildirim sağlamak düğmesine sekme](media/vs-2019/vs-installer-report-problem.png)
3. Sorun raporunuza bir başlık verin ve ilgili ayrıntıları sağlayın. Tıklayın **sonraki** gitmek için **ekleri** bölümüne ve ardından oluşturulan günlük dosyasını ekleyin (dosya altındadır genellikle `%TEMP%\vslogs.zip`).
4. Tıklayın **sonraki** sorun raporunuzu gözden geçirin ve ardından **Gönder**.

::: moniker-end

### <a name="step-5---run-installcleanupexe-to-remove-installation-files"></a>Adım 5 - Çalıştır InstallCleanup.exe yükleme dosyalarını kaldırmak için

Son çare yapabilecekleriniz [Visual Studio kaldırmak](remove-visual-studio.md) tüm yükleme dosyalarını ve ürün bilgileri kaldırmak için.

1. Bölümündeki yönergeleri [Kaldır Visual Studio](remove-visual-studio.md).
2. Açıklanan önyükleyici yeniden [adım 3 - yükseltme sorunlarını gidermek için Visual Studio yükleyicisi dizini silme](#step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems).
3. Yükleme veya Visual Studio güncelleştirmeyi yeniden deneyin.

### <a name="step-6---contact-us-optional"></a>6\. adım - (isteğe bağlı) bizimle iletişime geçin

Önceki adımlardan hiçbiri başarılı bir şekilde yardımcı, yükleme veya yükseltme Visual Studio, kullanarak bizimle iletişime geçin bizim [ **canlı sohbet** ](https://visualstudio.microsoft.com/vs/support/#talktous) seçeneği (yalnızca İngilizce) daha fazla yardım için destek.

## <a name="offline-installations"></a>Çevrimdışı yüklemeler

Aşağıda, bir [çevrimdışı yükleme](create-an-offline-installation-of-visual-studio.md) oluştururken ve sonra yerel bir düzenden yüklerken size yardımcı olabilecek bilinen sorunların ve bazı geçici çözümlerin bir tablosu verilmiştir.

| Sorun       | Öğe                   | Çözüm |
| ----------- | ---------------------- | -------- |
| Kullanıcılar dosyalara erişimi yoktur. | izinleri (ACL) | Bunlar diğer kullanıcılara Okuma yetkisi vermek için izinleri (ACL) ayarlayın sağlayın *önce* çevrimdışı yükleme paylaşın. |
| Yeni iş yükleri, bileşenleri ve dil yüklenemedi.  | `--layout`  | Kısmi bir düzenden yükleme ve daha önce iş yükleri, bileşenler veya indirilmedi diller, kısmi düzeni'ni seçin, internet erişimi olduğundan emin olun. |

Bir [ağ yüklemesiyle](create-a-network-installation-of-visual-studio.md)ilgili sorunları çözme hakkında daha fazla bilgi için bkz. [Visual Studio 'yu yüklerken veya kullanırken ağla Ilgili hatalarda sorun giderme](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="installation-logs"></a>Yükleme günlükleri

Kurulum günlükleri, çoğu yükleme sorunlarını gidermek için gereklidir. Ne zaman gönderdiğiniz bir sorun kullanarak [sorun bildir](../ide/how-to-report-a-problem-with-visual-studio.md) Visual Studio Yükleyicisi ', bu günlükleri otomatik olarak, rapora dahil edilir.

Microsoft Support başvurursanız kullanarak bu ayar günlüklerini göndermeniz gerekebilir [Microsoft Visual Studio ve .NET Framework günlük toplama aracı](https://www.microsoft.com/download/details.aspx?id=12493). Günlük toplama aracı, Visual Studio tarafından yüklenen .NET Framework, Windows SDK ve SQL Server dahil tüm bileşenlerin kurulum günlüklerini toplar. Ayrıca, bilgisayar bilgilerini, Windows Installer envanterini ve Visual Studio yükleyicisi, Windows Installer ve sistem geri yükleme için Windows olay günlüğü bilgilerini toplar.

Günlükleri toplamak için:

1. [Aracı indirmek](https://www.microsoft.com/download/details.aspx?id=12493).
2. Bir yönetici komut istemi açın.
3. Çalıştırma `Collect.exe` aracı kaydettiğiniz dizinden.
4. Ortaya çıkan Bul `vslogs.zip` dosyası, `%TEMP%` dizine, örneğin, `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`.

> [!NOTE]
> Aracı altında başarısız yüklemenin çalıştırıldığı kullanıcı hesabı altında çalıştırılması gerekir. Aracı farklı bir kullanıcı hesabından çalıştırıyorsanız, `–user:<name>` altında başarısız yüklemenin çalıştırıldığı kullanıcı hesabı belirtmek için seçeneği. Çalıştırma `Collect.exe -?` ek seçenekler ve kullanım bilgileri için bir yönetici komut isteminden.

## <a name="live-help"></a>Canlı yardım

Bu sorun giderme Kılavuzu'nda listelenen çözümleri başarıyla yüklemeniz veya Visual Studio yükseltme, kullanmanız için size yardımcı bizim [ **canlı sohbet** ](https://visualstudio.microsoft.com/vs/support/#talktous) seçeneği (yalnızca İngilizce) daha fazla yardım için destek.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 'Yu kaldır](remove-visual-studio.md)
* [Yükleme ve bir güvenlik duvarı veya proxy sunucusunun arkasına Visual Studio ve Azure hizmetlerini kullanma](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Visual Studio Yönetici Kılavuzu](visual-studio-administrator-guide.md)
