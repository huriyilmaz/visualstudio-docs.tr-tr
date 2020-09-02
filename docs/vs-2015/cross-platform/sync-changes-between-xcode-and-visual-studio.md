---
title: XCode ve Visual Studio 2015 arasındaki değişiklikleri eşitleyin | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c71a4d7c-120e-4559-a114-3a99c4b860a9
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 42352ba4c5260c4b13a4cb3c6875d3469efcf404
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62573400"
---
# <a name="sync-changes-between-xcode-and-visual-studio"></a>XCode ve Visual Studio Arasındaki Eşitleme Değişiklikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mobil geliştirme bileşeni için Microsoft Visual C++, bilgisayarınız ile Mac 'niz arasında çalışmanızı eşitlemeye yönelik uzak özellikleri içerir. Visual Studio ve Mac makineleriniz eşlendiğinde, Visual Studio 'da projenizi XCode 'da açmak, kodunuzu XCode ve Visual Studio arasında taşımak ve geçici XCode proje dizinini temizlemek için kullanabileceğiniz yeni seçenekler vardır.

 Uzak makine seçeneklerini kullanmak için projenizin bir iOS uygulama projesi olması ve Visual Studio 'Nun Mac ile eşleştirilmelidir. Bir Mac 'i eşleştirmeye ilişkin Önkoşullar ve yönergeler için bkz. [iOS kullanarak derlemek Için araçları yükleyip yapılandırma](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="the-remote-machine-menu"></a>Uzak makine menüsü
 **Çözüm Gezgini**, bağlam menüsünü göstermek Için bir iOS uygulama projesine sağ tıklayın. Kullanılabilir uzak seçenekleri göstermek için **uzak makine** öğesini seçin.

 ![Çözüm Gezgini uzak makine menü öğesi](../cross-platform/media/cppmdd-u2-remotemachine-menu.jpg "CPPMDD_U2_RemoteMachine_Menu")

 Bu komutlar, projenizi XCode 'da açmanıza, yerel değişiklikleri veya tüm projeyi Visual Studio ile XCode arasında taşımanıza ve uzak makinedeki geçici dosyaları temizleyebilmesine olanak sağlar.

### <a name="open-in-xcode"></a>XCode 'da aç
 Projeyi XCode 'da Visual Studio 'dan açmak için, **uzak makine** alt menüsünde, eşlenen uzak makinede seçili projeyi açmak Için **Xcode 'da aç** ' ı seçin. Vcremote sunucusu Mac 'inizde XCode 'u açmak için kullanılır ve Mac 'inizde projenin bir kopyasını içeren geçici bir dizine gidin. Visual Studio, proje için kullanılan geçici dizini gösteren bir iletişim kutusu açılır. Uzak makinede gerçekleştirilen eylemler, Visual Studio 'daki **Çıkış** penceresinde de gösterilir. Bunları görmek için **Çıkış** penceresinin en üstündeki açılan **listeden çıktıyı göster** ' ın yanındaki **Visual C++ uzak makine** ' yi seçmeniz gerekebilir.

 ![Çıkış penceresi, uzak makine eylemlerini gösterir.](../cross-platform/media/cppmdd-u2-remotemachine-output.png "CPPMDD_U2_RemoteMachine_Output")

 Mac 'inizde, kodunuzu ve kaynaklarınızı, film şeritlerinizi ve eylemlerinizi düzenlemek için tüm XCode araçlarını kullanabilirsiniz. Visual Studio 'da, uzak makinede değişikliklerin yapıldığını belirtmek için iOS uygulama projenize "XCode içinde açılan" ile açıklama eklenir. Düzenlemeleriniz tamamlandıktan sonra, değişiklikleri Visual Studio projenize geri kopyalamak için uzak veya artımlı çekme aracılığıyla uzak komutlardan çekme seçeneğini kullanabilirsiniz.

### <a name="push-to-remote-and-incremental-push-to-remote"></a>Uzak ve artımlı gönderimi uzak 'a gönder
 Visual Studio 'da iOS uygulama projenizde değişiklik yaptıysanız, değiştirilen proje dosyalarını eşleştirilmiş uzak makineye taşımak için uzak ve artımlı gönderimi uzak komutlara Gönder ' i kullanabilirsiniz. Uzak komuta gönderim, tüm proje dosyalarını uzak makineye kopyalar. Uzak komuta artımlı gönderimi yalnızca değiştirilen dosyaları uzak makineye kopyalar. Küçük değişikliklerle büyük projeler için, artımlı komut zaman ve bant genişliği tasarrufu sağlayabilir.

 Proje dosyalarını Mac 'nize kopyalamak için, Visual Studio 'da **Çözüm Gezgini** penceresinde, içerik menüsünü açmak Için iOS uygulama projesine sağ tıklayın. **Uzak makine** ' yi seçin ve proje dosyalarını Visual Studio 'dan **Mac 'e kopyalamak için uzak ya da** **artımlı gönder** ' i seçin.

### <a name="pull-from-remote-and-incremental-pull-from-remote"></a>Uzak ve artımlı alma 'dan uzaktan çekin
 XCode 'da projenizde değişiklik yaptıktan sonra, projeleri eşitlenmiş halde tutmak için değişiklikleri Visual Studio 'ya geri taşıyın.

 Proje dosyalarını Mac 'Inizden kopyalamak için, Visual Studio 'da **Çözüm Gezgini** penceresinde, içerik menüsünü açmak Için iOS uygulama projesine sağ tıklayın. **Uzak makineyi** seçin ve proje dosyalarını Mac 'Inizden Visual Studio 'ya kopyalamak için **uzak veya** **artımlı** alma seçeneklerinden birini belirleyin.

### <a name="clean-remote"></a>Uzak öğeyi temizle
 Uzak makinedeki geçici proje dizinindeki dosyaları silmek için temizle uzak komutunu kullanabilirsiniz. Kaynak dosya veya derleme ürünleri dahil olmak üzere dizin içeriği Mac 'inizde kaldırılır. Temiz uzak komutunu kullanmadan önce uzak veya artımlı çekme 'yi kullanarak Visual Studio 'ya geri dönmek istediğiniz değişiklikleri eşitlediğinizden emin olun.

 Uzak makinedeki geçici proje dizinini temizlemek için, Visual Studio 'da **Çözüm Gezgini** penceresinde, içerik menüsünü açmak Için iOS uygulama projesine sağ tıklayın. Mac 'Inizden proje dizin dosyalarını kaldırmak için **uzak makine** ' yi seçin ve **Uzaktan temizle** ' yi seçin.
