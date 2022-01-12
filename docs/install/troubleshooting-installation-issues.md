---
title: Yükleme veya yükseltme sorunlarını giderme
description: Bazen işler ters gidebilir. Yükleme veya Visual Studio başarısız olursa, bu sayfa yardımcı olabilir.
ms.date: 09/14/2021
ms.custom: vs-acquisition
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 757b8f8c01145d2ec8c0a71105d19e3e76549953
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135803862"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Yükleme Visual Studio yükseltme sorunlarını giderme

> [!IMPORTANT]
> Yüklemeyle ilgili sorun mu var? Size yardımcı olabiliriz. Yükleme sohbeti [**(yalnızca**](https://visualstudio.microsoft.com/vs/support/#talktous) İngilizce) destek seçeneği sunuyoruz.

Bu sorun giderme kılavuzu, yükleme sorunlarının çoğunu çözmesi gereken adım adım yönergeleri içerir.

## <a name="online-installations"></a>Çevrimiçi yüklemeler

Aşağıdaki adımlar tipik bir çevrimiçi yükleme için geçerlidir. Çevrimdışı yükleme için [bkz. Çevrimdışı yükleme sorunlarını giderme.](#offline-installations)

### <a name="step-1---check-whether-the-problem-is-a-known-issue"></a>1. Adım: Sorunun bilinen bir sorun olup olmadığını denetleme

::: moniker range="vs-2017"

Microsoft'un düzeltme üzerinde Visual Studio Yükleyicisi bazı bilinen sorunlar vardır. Soruna geçici bir çözüm olup olamay için sürüm [notlarımızın Bilinen Sorunlar bölümüne bakın.](/visualstudio/releasenotes/vs2017-relnotes#-known-issues)

::: moniker-end

::: moniker range="vs-2019"

Microsoft'un düzeltme üzerinde Visual Studio Yükleyicisi bazı bilinen sorunlar vardır. Soruna geçici bir çözüm olup olamay için sürüm [notlarımızın Bilinen Sorunlar bölümüne bakın.](/visualstudio/releases/2019/release-notes#-known-issues)

::: moniker-end

::: moniker range=">=vs-2022"

Microsoft'un düzeltme üzerinde Visual Studio Yükleyicisi bazı bilinen sorunlar vardır. Sorun çözüldüğünü kontrol edin veya sürüm notlarımızın Bilinen Sorunlar [bölümünde geçici çözümleri bulun.](/visualstudio/releases/2022/release-notes#-known-issues)

::: moniker-end

### <a name="step-2---try-repairing-visual-studio"></a>2. Adım- 2. Adım: Visual Studio

Onarım, sık karşılaşılan birçok güncelleştirme sorununa çözüm sağlar. Çalışma zamanlarını onarma ve onarma hakkında daha fazla Visual Studio [bkz. Visual Studio.](repair-visual-studio.md)

### <a name="step-3---check-with-the-developer-community"></a>3. Adım: Geliştirici topluluğuna göz at

[Visual Studio Developer Community](https://aka.ms/feedback/suggest?space=8) arama. Topluluğun diğer üyeleri, soruna yönelik bir çözüm veya geçici çözüm bulmuş olabilir.

### <a name="step-4---delete-the-visual-studio-installer-folder-to-fix-upgrade-problems"></a>4. Adım: Yükseltme Visual Studio Yükleyicisi için Visual Studio Yükleyicisi klasörünü silme

Visual Studio Yükleyicisi önyükleyicisi, dosyanın yüklemesi başlatan hafif bir yürütülebilir Visual Studio Yükleyicisi. Uygulama Visual Studio Yükleyicisi ve ardından önyükleyiciyi yeniden çalıştırma bazı güncelleştirme hatalarını çözer.

> [!NOTE]
> Aşağıdaki eylemlerin gerçekleştirerek Visual Studio Yükleyicisi yeniden yüklenir ve yükleme meta verileri sıfırlanır.

::: moniker range="vs-2017"

1. Visual Studio Yükleyicisi’ni kapatın.
1. Yükleme Visual Studio Yükleyicisi silin. Genellikle dizini `C:\Program Files (x86)\Microsoft Visual Studio\Installer` olur.
1. Önyükleyiciyi Visual Studio Yükleyicisi çalıştırın. Önyükleyiciyi İndirilenler klasörünüzde bir desenden sonra bir dosya adıyla `vs_[Visual Studio edition]__*.exe` bulabilirsiniz. Bu uygulamayı bulamazsanız, Visual Studio indirmeleri sayfasına gidip [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sürümünüz için İndir'e  tıklayarak önyükleyiciyi indirebilirsiniz. Ardından, yükleme meta verilerinizi sıfırlamak için yürütülebilir dosyayı çalıştırın.
1. Yeniden yükleme veya güncelleştirme Visual Studio deneyin. Yükleyici başarısız olursa sonraki adıma gidin.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio Yükleyicisi’ni kapatın.
1. Visual Studio Yükleyicisi silin. Genellikle dizini `C:\Program Files (x86)\Microsoft Visual Studio\Installer` olur.
1. Önyükleyiciyi Visual Studio Yükleyicisi çalıştırın. Önyükleyiciyi İndirilenler klasörünüzde bir desenle eşleşen bir dosya adıyla `vs_[Visual Studio edition]__*.exe` bulabilirsiniz. Bu uygulamayı bulamazsanız, Visual Studio indirmeleri sayfasına gidip [Visual Studio](https://visualstudio.microsoft.com/downloads) sürümünüz için İndir'e  tıklayarak önyükleyiciyi indirebilirsiniz. Ardından, yükleme meta verilerinizi sıfırlamak için yürütülebilir dosyayı çalıştırın.
1. Yeniden yükleme veya güncelleştirme Visual Studio deneyin. Yükleyici başarısız olursa sonraki adıma gidin.

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio Yükleyicisi’ni kapatın.
1. Visual Studio Yükleyicisi silin. Genellikle klasör yolu `C:\Program Files (x86)\Microsoft Visual Studio\Installer` olur.
1. Önyükleyiciyi Visual Studio Yükleyicisi çalıştırın. Önyükleyiciyi İndirilenler **klasörünüzde** bir desenle eşleşen bir dosya adıyla `vs_[Visual Studio edition]__*.exe` bulabilirsiniz. Veya Visual Studio indirme sayfasından Visual Studio sürümünüz [için Visual Studio indirebilirsiniz.](https://visualstudio.microsoft.com/downloads) Ardından, yükleme meta verilerinizi sıfırlamak için yürütülebilir dosyayı çalıştırın.
1. Yeniden yükleme veya güncelleştirme Visual Studio deneyin. Sorun Visual Studio Yükleyicisi devam ederse Sorun bildirme [adımına geçin.](#step-5---report-a-problem)

::: moniker-end

### <a name="step-5---report-a-problem"></a>5. Adım - Sorun bildirme

Bazı durumlarda, örneğin bozuk dosyalar olduğunda sorunlar için büyük/büyük/büyük harf sorun gidermesi gerekli olabilir. Size yardımcı olmak için şu adımları izleyin:

::: moniker range="vs-2017"

1. Kurulum günlüklerinizi toplayın. Ayrıntılar [için bkz. Visual Studio yükleme günlüklerini](#installation-logs) nasıl edinebilirsiniz?
1. Visual Studio Yükleyicisi'yi açın ve sorun **bildirin'e** tıklar ve Visual Studio geri bildirim aracını açın.
![Uygulamanın geri bildirim sağla düğmesini gösteren Visual Studio Yükleyicisi.](media/report-a-problem.png)
1. Sorun raporunuz için bir başlık girin ve ilgili ayrıntıları girin. Ekler **bölümüne** gitmek için **Sonraki'ne** tıklayın ve oluşturulan günlük dosyasını (genellikle dosyanın olduğu yer) iliştirin. `%TEMP%\vslogs.zip`
1. Sorun **raporunu gözden** geçirmek için Sonraki'ne ve ardından Gönder'e **tıklayın.**

::: moniker-end

::: moniker range="vs-2019"

1. Kurulum günlüklerinizi toplayın. Ayrıntılar [için bkz. Visual Studio yükleme günlüklerini](#installation-logs) nasıl edinebilirsiniz?
1. Visual Studio Yükleyicisi'yi açın ve sorun **bildirin'e** tıklar ve Visual Studio geri bildirim aracını açın.
![Uygulamanın geri bildirim sağla düğmesini gösteren Visual Studio Yükleyicisi.](media/vs-2019/vs-installer-report-problem.png)
1. Sorun raporunuz için bir başlık girin ve ilgili ayrıntıları girin. Ekler **bölümüne** gitmek için **Sonraki'ne** tıklayın ve oluşturulan günlük dosyasını (genellikle dosyanın olduğu yer) iliştirin. `%TEMP%\vslogs.zip`
1. Sorun **raporlarınızı** gözden geçirmek için Sonraki'ne ve ardından **Gönder'e tıklayın.**

::: moniker-end

::: moniker range=">=vs-2022"

1. Kurulum günlüklerinizi toplayın. Ayrıntılar [için bkz. Visual Studio yükleme günlüklerini](#installation-logs) nasıl edinebilirsiniz?
1. Visual Studio Yükleyicisi'yi açın ve Sorun **bildirin'i** seçen Visual Studio geri bildirim aracını açın.
![Uygulamanın geri bildirim sağla düğmesini gösteren Visual Studio Yükleyicisi.](media/vs-2022/vs-installer-report-problem.png)
1. Sorun raporunuz için bir başlık girin ve ilgili ayrıntıları girin. Uygulamanın en son kurulum Visual Studio Yükleyicisi otomatik olarak sorun **rapornizin Ek ekler** bölümüne eklenir.
1. **Gönder'i seçin.**

::: moniker-end

### <a name="step-6---remove-visual-studio-installation-files"></a>6. Adım - Visual Studio dosyalarını kaldırma

Son bir tesis olarak, tüm yükleme Visual Studio ve ürün bilgilerini kaldırabilirsiniz:

1. Bu makaledeki adımları izleyin: [Visual Studio](uninstall-visual-studio.md#remove) kaldırın.
1. Önyükleyiciyi Visual Studio Yükleyicisi yeniden çalıştırma. Önyükleyiciyi İndirilenler **klasörünüzde** bir desenle eşleşen bir dosya adıyla `vs_[Visual Studio edition]__*.exe` bulabilirsiniz. Veya Visual Studio indirme sayfasından Visual Studio sürümünüz [için Visual Studio indirebilirsiniz.](https://visualstudio.microsoft.com/downloads)
1. Yeniden yüklemeyi deneyin Visual Studio.

### <a name="step-7---contact-us-optional"></a>7. Adım - Bize ulaşın (isteğe bağlı)

Önceki adımlardan hiçbiri, yüklemenizi veya yükseltmenizi başarıyla Visual Studio, [](https://visualstudio.microsoft.com/vs/support/#talktous) daha fazla yardım için canlı sohbet destek seçeneğimizi (yalnızca İngilizce) kullanarak bizimle iletişime geçin.

## <a name="offline-installations"></a>Çevrimdışı yüklemeler

Çevrimdışı yükleme ve yerel bir düzenden yükleme işlemi sırasında size yardımcı olacak bazı bilinen sorunlar [ve](create-an-offline-installation-of-visual-studio.md) geçici çözümler burada ve bulunmaktadır.

| Sorun       | Çözüm |
| ----------- | -------- |
| Kullanıcılar dosyalara erişe | Çevrimdışı yüklemeyi paylaşmadan önce diğer kullanıcılara  okuma erişimi vermek için izinleri (ACL' *ler)* ayarlayasınız. |
| Yeni iş yükleri, bileşenler veya dil paketleri yük devretmedi | Kısmi bir düzenden yükleme yaptıysanız ve bu kısmi düzen için daha önce indirilmiş olmayan iş yüklerini, bileşenleri veya dilleri seçerek İnternet erişiminiz olduğundan emin olun. |

Bir ağ yüklemesi ile [ilgili sorunları çözmek için](create-a-network-installation-of-visual-studio.md) [bkz.](troubleshooting-network-related-errors-in-visual-studio.md)ağ ile ilgili sorunları gidermek için Visual Studio.

## <a name="installation-logs"></a>Yükleme günlükleri

Kurulum günlükleri, yükleme sorunlarının çoğunu gidermenize yardımcı olur. Sorun Bildir'i [kullanarak](../ide/how-to-report-a-problem-with-visual-studio.md) bir sorun gönderdiğinizde Visual Studio Yükleyicisi için en son kurulum Visual Studio Yükleyicisi otomatik olarak raporunuza eklenir.

Microsoft Desteği başvurursanız, [Microsoft Visual Studio ve .NET Framework günlük toplama aracını](https://www.microsoft.com/download/details.aspx?id=12493)kullanarak kurulum günlüklerini toplamanız istenebilir. günlük toplama aracı, .NET Framework, Windows SDK ve SQL Server dahil olmak üzere Visual Studio tarafından yüklenen tüm bileşenlerden kurulum günlüklerini toplar. ayrıca bilgisayar bilgilerini, Windows Installer envanterini ve Visual Studio Yükleyicisi, Windows Installer ve sistem geri yükleme için olay günlüğü bilgilerini Windows toplar.

Günlükleri toplamak için:

1. [Aracı indirin](https://www.microsoft.com/download/details.aspx?id=12493).
1. Bir yönetim komut istemi açın.
1. `Collect.exe`Aracını kaydettiğiniz klasörde çalıştırın.
1. Araç `vslogs.zip` `%TEMP%` , klasörünüzde genellikle adresinde bir dosya oluşturur `C:\Users\YourName\AppData\Local\Temp\vslogs.zip` .

> [!NOTE]
> Aracın, başarısız olan yüklemenin çalıştırıldığı Kullanıcı hesabı altında çalıştırılması gerekir. Aracı farklı bir kullanıcı hesabından çalıştırıyorsanız, `–user:<name>` başarısız olan yüklemenin çalıştırıldığı Kullanıcı hesabını belirtme seçeneğini belirleyin. `Collect.exe -?`Ek seçenekler ve kullanım bilgileri için yönetici komut isteminden çalıştırın.

## <a name="live-help"></a>Canlı yardım

bu sorun giderme kılavuzunda listelenen çözümler Visual Studio başarıyla yüklemenize veya yükseltmenize yardımcı değilse, daha fazla yardım için [**canlı sohbet**](https://visualstudio.microsoft.com/vs/support/#talktous) desteği seçeneğini kullanın (yalnızca ingilizce).

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio’yu onarın](repair-visual-studio.md)
* [Visual Studio kaldır](uninstall-visual-studio.md#remove)
* [Visual Studio ve Azure hizmetlerini bir güvenlik duvarı veya proxy sunucusunun arkasında yükleyip kullanma](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Visual Studio örneklerini algılamaya ve yönetmeye yönelik araçlar](tools-for-managing-visual-studio-instances.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)