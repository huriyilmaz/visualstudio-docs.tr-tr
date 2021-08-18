---
description: Artık Visual Studio Snapshot Debugger hizmetinize bağlandı ve hata ayıklamaya yardımcı olmak için anlık görüntüler toplamaya başlayabilirsiniz.
title: Sayfanın başlangıç Snapshot Debugger
ms.date: 07/14/2018
robots: noindex, nofollow
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2aa185a0f9bb59661670bb80970ec967dc9ea30e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090583"
---
# <a name="getting-started-with-the-snapshot-debugger"></a>Başlarken ile Snapshot Debugger

Artık Visual Studio Snapshot Debugger hizmetinize bağlandı ve hata ayıklamaya yardımcı olmak için anlık görüntüler toplamaya başlayabilirsiniz.

Bu Snapshot Debugger kullanmak için kodunda bazı anlık görüntüler ayarlayın, düğmeye tıklayarak anlık görüntüleri toplamaya başlayabilir ve ardından senaryoyu çalıştırabilirsiniz. Kod çalıştırılarak bir anlık görüntü ayar güvenlik noktası ayarlanırsa, uygulamanın anlık görüntüsü alınır. Ardından anlık görüntüyü açmak için Visual Studio penceresinde Tanılama Araçları açın. Artık anlık görüntüde yerel olduğu gibi hizmetinizin hata ayıklaması da abilirsiniz. Ayrıntılı yönergeler için okumaya devam edin.

## <a name="collect-and-view-snapshots"></a>Anlık görüntüleri toplama ve görüntüleme

Uygulama Snapshot Debugger anlık görüntüleri toplar. Anlık görüntüler, zaman içinde bir noktadaki uygulama resimleriniz gibi olur. Kodda bir Visual Studio noktası ayarlayan bir anlık görüntü ne zaman ve nerede toplaymları hakkında bilgi veresiniz. Ek bileşende, araştıran sorunun anlık görüntüsünü almak için gereken tüm koşulları ayarlayın.

### <a name="set-a-snappoint"></a>Anlık Bileşen Ayarlama

1. Kod düzenleyicisinde, bir ek bileşen ayarlamak için ilgilendiğimiz bir kod çizgisinin yanındaki sol olukluna tıklayın. Bu kodun çalıştırılamayacak olduğundan emin olun.

    ![Düzenleyicide ek bileşen ayarlama](../media/snapshot-startpage-set-snappoint.png)

    Sol tarafta mor bir altıgen görünür.

2. Ek **bileşeni açmak** için Koleksiyonu Başlat'a tıklayın.

### <a name="open-a-snapshot"></a>Anlık Görüntü Açma

1. Anlık görüntüye isabetlendiğinde, sağ Tanılama Araçları anlık görüntü görüntülenir. Pencere açılmazsa, Hata ayıkla'ya tıklayın ve  >  **Windows'Tanılama Araçları.**  >  

    ![Tanılama Araçları penceresindeki anlık görüntü](../media/snapshot-startpage-diagsession-window.png)

2. Anlık görüntüyü açmak için çift tıklayın.

### <a name="inspect-snapshot-data"></a>Anlık görüntü verilerini inceleme

Bu görünümden değişkenlerin üzerine gelerek DataTips'i görüntüleyebilirsiniz, YerelLer, İzlemeler ve Çağrı Yığını pencerelerini kullanabilir ve ifadeleri değerlendirebilirsiniz.

Web sitesinin kendisi hala canlıdır ve son kullanıcılar etkilenmez. Varsayılan olarak, anlık görüntü her anlık görüntüde yakalanır. Başka bir ifadeyle, anlık görüntü yakalanır ve anlık görüntü yakalanır. Ek bileşende başka bir anlık görüntü yakalamak için, Koleksiyonu Güncelleştir'e tıklayarak anlık görüntüyü **yeniden açabilirsiniz.**

### <a name="set-a-logpoint"></a>Günlük Noktası Ayarlama

1. Bir ek bileşen simgesine (mor altıgen) sağ tıklayın ve **Ayarlar.**

2. Anlık Ek **Bileşen Ayarlar** Eylemler'i **seçin.**

    ![Ek bileşen koşulları](../media/snapshot-startpage-logpoint.png)

3. İleti **alanına,** günlüğe almak istediğiniz bir günlük iletisi girin. Ayrıca günlük iletinizin değişkenlerini küme ayraçlarına yerleştirerek de değerlendirebilirsiniz.

    **Çıkış Penceresi'a gönder'i** seçerseniz, günlük Tanılama Araçları isabet olduğunda ileti Tanılama Araçları penceresinde görüntülenir.

    Uygulama günlüğüne **gönder'i** seçerseniz, ileti, günlüğe isabetlendiğinde App Analizler gibi iletilerde `System.Diagnostics.Trace` (veya `ILogger` .NET Core'da) gördüğünüz her yerde görüntülenir.

## <a name="learn-more"></a>Daha Fazla Bilgi Edinin

Belge sayfası hakkında daha fazla Snapshot Debugger belgeler [sayfasında bulabilirsiniz.](../debug-live-azure-applications.md) Hataları bulmayı kolaylaştırmak için koşulları ayarlama hakkında daha fazla bilgi öğrenin.

## <a name="dont-show-me-this-again"></a>Bunu Bir Daha Gösterme

Snapshot Debugger'a bağlanarak Snapshot Debugger'i bir daha göstermeyebilirsiniz. Snapshot Debugger Araçlar Seçenekler sayfasında oturum **Başlarken'** sayfasını   >    >  **Snapshot Debugger.**

![Snapshot Debugger Aracı Seçenek Sayfası](../media/snapshot-startpage-tools-options.png)
