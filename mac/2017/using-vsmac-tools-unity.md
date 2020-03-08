---
title: Visual Studio için Unity için Mac araçları kullanarak
description: Bu kılavuz, Mac araçları için Unity uzantısı için Visual Studio kullanmayı açıklar
author: therealjohn
ms.author: johmil
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: d4df59273db1fab8492b36e87e48e0e770072f17
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408549"
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Visual Studio için Unity için Mac araçları kullanarak

Bu bölümde, Visual Studio Mac araçları için Unity'nın tümleştirme ve verimlilik özellikleri için nasıl kullanacağınızı ve Mac hata ayıklayıcının Unity geliştirme için Visual Studio kullanmayı öğreneceksiniz.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Mac için Visual Studio'da Unity betikleri açma

Mac için Visual Studio [Unity için dış betik düzenleyicisi olarak](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac)ayarlandıktan sonra, Unity düzenleyiciden herhangi bir betiği açmak, seçilen komut dosyası açık olarak otomatik olarak başlatılır veya Mac için Visual Studio.

Alternatif olarak, Mac için Visual Studio Unity 'de **varlıklar** menüsünden **Proje Aç C#**  ' ı seçerek kaynak düzenleyicide açık betik olmadan açılabilir.

![C# proje Aç](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Unity belgeleri erişimi

Unity için Araçlar Mac için Visual Studio Unity API belgelerini erişmek için bir kısayol içerir. Mac için Visual Studio Unity API belgelerine erişmek için, imleci hakkında bilgi almak istediğiniz Unity API 'sine yerleştirin ve **⌘ Command + '** tuşlarına basın.

## <a name="intellisense-for-unity-messages"></a>Unity özellikleri için IntelliSense
Unity motoru, tek davranış betiklerine ileti yayınlar, geliştiricilerin OnMouseDown, OnTriggerEnter vb. gibi iletilere yeniden davranan kodu yazmasına izin verir. Bunlar, temel Monodavranış sınıfında sanal metotlar olmadığından, MonoDevelop gibi bazı IDE 'Ler Unity iletileri için kod tamamlama işlevselliği olmamasıdır.

Ancak, Visual Studio için Unity için Mac araçları Unity iletileri için IntelliSense işlevselliği genişletir. Unity iletilerini Uygula MonoBehaviour betiklerde daha kolay hale getirir ve Unity API öğrenmeye yardımcı olur. Unity iletileri için IntelliSense kullanmak için:

1. MonoBehaviour türetilen bir sınıfın gövdesi içinde yeni bir satıra imleci yerleştirin.

2. `OnTriggerEnter`gibi bir Unity iletisinin adını yazmaya başlayın.

3. "**Azı tipi**" harfleri yazıldıktan sonra, IntelliSense önerilerindeki bir liste görüntülenir.

   ![IntelliSense Kullanma](media/using-vsmac-tools-unity-image2.png)

4. Seçim listesindeki üç yolla değiştirilebilir:

   * **Yukarı** ve **aşağı** ok tuşlarıyla.

   * İstenen öğe üzerinde fare ile tıklayarak.

   * İstenen öğe adı devam ederek.

5. IntelliSense, tüm gerekli parametreleri de dahil olmak üzere seçili Unity ileti ekleyebilirsiniz:

   * **Sekmesine**basarak.

   * **Return**tuşuna basarak.

   * Seçili öğeyi çift tıklayarak.

   ![Unity iletisi IntelliSense'de Ekle](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>Yeni Unity dosyaları ve klasörleri ekleme

Unity Düzenleyicisi'nde bir Unity projesi için her zaman yeni dosyaları ekleyebilirsiniz, ancak yeni Unity betikleri, gölgelendiriciler ve klasörlerinden Visual Studio'dan kolayca oluşturmak için Mac için Visual Studio sağlar.

### <a name="add-a-new-c-monobehaviour-script"></a>Yeni bir C# MonoBehaviour betik Ekle

Yeni C# bir monodavranış betiği eklemek Için, **varlıklar klasörüne** veya çözüm panelindeki alt dizinlerinden birine sağ tıklayın ve **Yeni > monodavranış Ekle**' yi seçin.

![Yeni MonoBehaviour Ekle](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>Yeni bir Unity gölgelendirici ekleme

Yeni bir Unity gölgelendiricisi eklemek için, **varlıklar klasörüne** veya çözüm panelindeki bir alt dizine sağ tıklayın ve **Yeni > gölgelendirici Ekle**' yi seçin.

### <a name="add-a-new-folder"></a>Yeni bir klasör Ekle

Yeni bir klasör eklemek için, **varlıklar klasörüne** veya çözüm panelindeki bir alt dizine sağ tıklayın ve **Yeni > Klasör Ekle**' yi seçin.

Bu eklemeler, Unity editor proje penceresinde yansıtılır.

### <a name="to-rename-a-file-or-folder"></a>Bir dosya veya klasörü yeniden adlandırmak için
Çözüm panelinde yeniden adlandırılacak öğeye **sağ tıklayın** ve **yeniden adlandır...** seçeneğini belirleyin.

> [!NOTE]
> Betik ile yeni bir Unity projesi varsa ve varlıklar klasörü Visual Studio'da Çözüm panelinde Mac için görünmez, bir ilk C# betiği Unity editor'ı ekleyin.

## <a name="unity-debugging"></a>Unity hata ayıklama

Mac için Visual Studio ile Unity projeleri ayıklanabilir

### <a name="start-debugging"></a>Hata Ayıklamayı Başlat

Hata ayıklamayı başlatmak için:

1. **Oynat** düğmesine tıklayarak Visual Studio 'yu Unity 'ye bağlayın veya **Command + Return**ya da **F5**yazın.

   ![Visual Studio'da Yürüt'e tıklayın](media/using-vsmac-tools-unity-image5.png)

2. Unity 'ye geçin ve oyunu düzenleyicide çalıştırmak için **Yürüt** düğmesine tıklayın.

   ![Unity Yürüt'e tıklayın](media/using-vsmac-tools-unity-image6.png)

3. Oyun bağlıyken, Visual Studio için Unity Düzenleyicisi'nde çalışırken karşılaşılan herhangi bir kesme noktası oyun yürütülmesini Duraklat ve burada oyun Mac için Visual Studio'da kesme noktası isabet kod satırının getirecek

### <a name="stop-debugging"></a>Hata ayıklamayı Durdur

Hata ayıklamayı durdurmak için:

1. Mac için Visual Studio **Durdur** düğmesine tıklayın veya **SHIFT + Command + Return**tuşlarına basın.

   ![Visual Studio'da Durdur'u tıklatın](media/using-vsmac-tools-unity-image7.png)

Mac için Visual Studio hata ayıklama hakkında daha fazla bilgi edinmek için bkz. [hata ayıklayıcıyı kullanma](debugging.md).
