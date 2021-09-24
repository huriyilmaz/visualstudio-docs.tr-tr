---
title: Visual Studio’yu onarın
titleSuffix: ''
description: Visual Studio 2017 yüklemesini onarmayı öğrenin
ms.date: 09/14/2021
ms.custom: vs-acquisition
ms.topic: how-to
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ca36dbefec8ff61a8ba05286f2dd8aa6593cc13b
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128374582"
---
# <a name="repair-visual-studio"></a>Visual Studio’yu onarın

bazen Visual Studio yüklemeniz hasar görmüşse veya bozulmuş olur. Güncelleştirme sorunları da dahil olmak üzere çok çeşitli yük-zamanlı sorunları düzeltmek için onarım yararlı olur.

## <a name="when-to-use-repair"></a>Onarma ne zaman kullanılır?

İle ilgili sorun yaşıyorsanız Onar 'ı kullanın:

* Diske bir dosya yazılırken meydana gelebilen yükleme yükü başarısız olur ve dosya bozulur. Onar, gerekli dosyaları yeniden alabilir.
* İstemci tarafı indirme: herhangi bir internet bağlantısı veya ara sunucu sorununu çözdüyoruz.
* Visual Studio güncelleştiriliyor. Onarma birçok yaygın güncelleştirme sorununu düzeltir.

> [!TIP] 
> Windows Installer gibi kararsız bir internet bağlantısı veya Windows hizmetindeki bir sorun, yüklemeye sorun oluşmasına neden olabilir. Bu senaryolarda, onarım de etkilenebilir. temel alınan sorunları denetlemek için Visual Studio Yükleyicisi tarafından oluşturulan hata raporunu gözden geçirin.

> [!NOTE] 
> Visual Studio onarma kullanıcı ayarlarını sıfırlar ve var olan derlemelerinizi yeniden yükler. bir ürün sorunuyla karşılaşıyorsanız ve onarmak sorunu gidermezse, bir [Visual Studio geri bildirim bileti](https://aka.ms/feedback/suggest?space=8)oluşturun. daha fazla bilgi için bkz. [Visual Studio veya Visual Studio Yükleyicisi ile ilgili sorun bildirme](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="how-to-repair"></a>Onarma
::: moniker range="vs-2017"

1. bilgisayarınızda **Visual Studio Yükleyicisi** bulun.

     örneğin, Windows 10 yıldönümü güncelleştirmesi veya sonraki bir sürümünü çalıştıran bir bilgisayarda **başlat**' ı seçin ve sonra da **Visual Studio Yükleyicisi** olarak listelendiği **V** harfine gidin.

   > [!NOTE]
   > bazı bilgisayarlarda Visual Studio Yükleyicisi, **Microsoft Visual Studio yükleyicisi** olarak **"d"** harfi altında listelenmiş olabilir.
   >
   > alternatif olarak, Visual Studio Yükleyicisi aşağıdaki konumda bulabilirsiniz:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Yükleyiciyi açın, **daha fazla**' yı seçin ve ardından **Onar**' ı seçin.

    ![Visual Studio Yükleyicisi daha fazla açılan menüsünde onarma seçeneğinin gösterildiği ekran görüntüsü.](media/repair-visual-studio.png "Visual Studio Yükleyicisi Visual Studio onar")

   > [!NOTE]
   > Visual Studio onarma ortamı sıfırlanır. Yükselme, Kullanıcı ayarları ve profiller olmadan yüklenen Kullanıcı başına uzantılar gibi yerel özelleştirmeler kaldırılır. Temalar, renkler, anahtar bağlamaları gibi eşitlenmiş ayarlarınız geri yüklenecek.
   >

   > [!TIP]
   > **Onarma** seçeneği yalnızca Visual Studio yüklü örnekleri için görünür. **onar** seçeneğini görmüyorsanız, Visual Studio Yükleyicisi listelenen bir sürümde "yüklü" yerine "kullanılabilir" olarak **daha fazla** seçim yapmış olursunuz.

::: moniker-end

::: moniker range="vs-2019"

1. bilgisayarınızda **Visual Studio Yükleyicisi** bulun.

     Windows Başlat menüsü, "yükleyici" için arama yapabilirsiniz.

     ![Visual Studio Yükleyicisi için Başlat menüsü aramasının sonucunu gösteren ekran görüntüsü.](media/vs-2019/visual-studio-installer.png "Visual Studio Yükleyicisi arayın")

     > [!NOTE]
     > aşağıdaki konumda Visual Studio Yükleyicisi de bulabilirsiniz:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Bu durumda, istemleri izleyin.

1. yükleyicide, yüklediğiniz Visual Studio sürümünü arayın. Daha sonra, **daha fazla**' yı ve ardından **Onar**' ı seçin.

     ![Visual Studio Yükleyicisi daha fazla açılan menüsünde onarma seçeneğinin gösterildiği ekran görüntüsü.](media/vs-2019/vs-installer-repair.png "Visual Studio onar 2019")

   > [!NOTE]
   > Visual Studio onarıldığında ortamı sıfırlanır. Yükselme, Kullanıcı ayarları ve profiller olmadan yüklenen Kullanıcı başına uzantılar gibi yerel özelleştirmeler kaldırılır. Temalar, renkler ve anahtar bağlamaları gibi eşitlenmiş ayarlarınız geri yüklenecek.
   >

   > [!TIP]
   > **Onarma** seçeneği yalnızca Visual Studio yüklü örnekleri için görünür. **onar** seçeneğini görmüyorsanız, Visual Studio Yükleyicisi listelenen bir sürümde "yüklü" yerine "kullanılabilir" olarak **daha fazla** seçim yapmış olursunuz.

::: moniker-end

::: moniker range=">=vs-2022"

1. bilgisayarınızda **Visual Studio Yükleyicisi** bulun.

     Windows Başlat menüsü, "yükleyici" araması yapın ve sonra sonuçlardan **Visual Studio Yükleyicisi** ' yı seçin.

     ![Visual Studio Yükleyicisi için Başlat menüsü aramasının sonucunu gösteren ekran görüntüsü.](media/vs-2022/vs-installer-search.png "Visual Studio Yükleyicisi arayın")

     > [!NOTE]
     > aşağıdaki konumda Visual Studio Yükleyicisi de bulabilirsiniz:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    devam etmeden önce Visual Studio Yükleyicisi güncelleştirmeniz istenebilir. Bu durumda, istemleri izleyin.

1. Visual Studio Yükleyicisi, onarmak istediğiniz Visual Studio yüklemeyi bulun. **Daha sonra diğer** açılan menüden **Onar** ' ı seçin.

     ![Visual Studio Yükleyicisi daha fazla açılan menüsünde onarma seçeneğinin gösterildiği ekran görüntüsü.](media/vs-2022/vs-installer-repair.png "Visual Studio onar 2022")

   > [!NOTE]
   > Visual Studio onarıldığında ortamı sıfırlanır. Yükseltme olmadan yüklenen Kullanıcı başına uzantılar gibi yerel özelleştirmeler, Kullanıcı ayarları ve profiller kaldırılır. Temalar, renkler ve anahtar bağlamaları gibi eşitlenmiş ayarlarınız geri yüklenecek.
   >

   > [!TIP]
   > **Onarma** seçeneği Visual Studio yüklü örneklerine uygulanır. **daha fazla** açılan menüde **onar** seçeneğini görmüyorsanız, Visual Studio Yükleyicisi **yüklü** sekmesi yerine **kullanılabilir** sekmeden mutluluk duyuyoruz.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
* [yükleme ve yükseltme sorunlarını giderme Visual Studio](troubleshooting-installation-issues.md)
