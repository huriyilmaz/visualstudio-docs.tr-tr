---
title: Unity için Mac için Visual Studio araçları kullanma
description: bu kılavuzda, Unity uzantısı için Mac için Visual Studio araçları 'nın nasıl kullanılacağı açıklanmaktadır
author: therealjohn
ms.author: johmil
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: 159929c2fcf4f6dc8fff28c4e88d8296a7a6ad8baa01c578d046b688b726d69d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121422367"
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Unity için Mac için Visual Studio araçları kullanma

bu bölümde, unity 'nin tümleştirme ve üretkenlik özellikleri için Mac için Visual Studio araçları kullanmayı ve unity geliştirme için Mac için Visual Studio hata ayıklayıcıyı kullanmayı öğreneceksiniz.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Mac için Visual Studio Unity betikleri açılıyor

Mac için Visual Studio [unity için dış betik düzenleyicisi olarak](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac)ayarlandıktan sonra, unity düzenleyiciden herhangi bir betiği açmak, seçilen komut dosyası açık olarak otomatik olarak başlatılır veya Mac için Visual Studio.

alternatif olarak, Mac için Visual Studio Unity 'de **varlıklar** menüsünden **C# Project aç** ' ı seçerek kaynak düzenleyicide açık betik olmadan açılabilir.

![C# projesini aç](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Unity belge erişimi

Mac için Visual Studio Unity araçları, Unity API belgelerine erişim için bir kısayol içerir. Mac için Visual Studio unity apı belgelerine erişmek için, imleci hakkında bilgi almak istediğiniz unity apı 'sine yerleştirin ve **⌘ command + '** tuşlarına basın.

## <a name="intellisense-for-unity-messages"></a>Unity iletileri için IntelliSense
Unity motoru, tek davranış betiklerine ileti yayınlar, geliştiricilerin OnMouseDown, OnTriggerEnter vb. gibi iletilere yeniden davranan kodu yazmasına izin verir. Bunlar, temel Monodavranış sınıfında sanal metotlar olmadığından, MonoDevelop gibi bazı IDE 'Ler Unity iletileri için kod tamamlama işlevselliği olmamasıdır.

ancak unity için Mac için Visual Studio araçları, ıntellisense işlevselliğini unity iletilerine genişletir. Bu, tek davranış betiklerine Unity iletilerinin uygulanmasını kolaylaştırır ve Unity API 'sini öğrenmeye yardımcı olur. Unity iletileri için IntelliSense 'i kullanmak için:

1. İmleci Monodavranış sınıfından türetilen bir sınıf gövdesinin içine yeni bir satıra yerleştirin.

2. Bir Unity iletisinin adını yazmaya başlayın, örneğin `OnTriggerEnter` .

3. "**Azı tipi**" harfleri yazıldıktan sonra, IntelliSense önerilerindeki bir liste görüntülenir.

   ![IntelliSense Kullanma](media/using-vsmac-tools-unity-image2.png)

4. Listedeki seçim üç şekilde değiştirilebilir:

   * **Yukarı** ve **aşağı** ok tuşlarıyla.

   * İstenen öğenin üzerine fareyle tıklanarak.

   * İstenen öğenin adını yazmaya devam edin.

5. IntelliSense, gerekli parametreler dahil olmak üzere seçili Unity iletisini ekleyebilir:

   * **Sekmesine** basarak.

   * **Return** tuşuna basarak.

   * Seçili öğeye çift tıklayarak.

   ![IntelliSense 'den Unity iletisi Ekle](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>Yeni Unity dosyaları ve klasörleri ekleme

unity düzenleyicisinde bir unity projesine her zaman yeni dosyalar ekleyebilmeniz için Mac için Visual Studio Visual Studio içinden kolayca yeni Unity betikleri, gölgelendiriciler ve klasörler oluşturulmasına olanak sağlar.

### <a name="add-a-new-c-monobehaviour-script"></a>Yeni bir C# monodavranış betiği ekleyin

Yeni bir C# monodavranış betiği eklemek için, **varlıklar klasörüne** veya alt dizinlerinden birine sağ tıklayıp çözüm panelinde bir tane **ekleyin ve yeni > monodavranış Ekle**' yi seçin.

![Yeni Monodavranış Ekle](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>Yeni bir Unity gölgelendiricisi ekleme

Yeni bir Unity gölgelendiricisi eklemek için, **varlıklar klasörüne** veya çözüm panelindeki bir alt dizine sağ tıklayın ve **Yeni > gölgelendirici Ekle**' yi seçin.

### <a name="add-a-new-folder"></a>Yeni klasör ekle

Yeni bir klasör eklemek için, **varlıklar klasörüne** veya çözüm panelindeki bir alt dizine sağ tıklayın ve **Yeni > klasör ekle**' yi seçin.

bu eklemeler, Unity düzenleyicisinin Project penceresinde yansıtılır.

### <a name="to-rename-a-file-or-folder"></a>Bir dosya veya klasörü yeniden adlandırmak için
Çözüm panelinde yeniden adlandırılacak öğeye **sağ tıklayın** ve **yeniden adlandır...** seçeneğini belirleyin.

> [!NOTE]
> komut dosyası içermeyen yeni bir Unity projeniz varsa ve varlıklar klasörü Mac için Visual Studio çözüm panelinde görünmüyorsa, Unity düzenleyicisi içinden bir ilk C# betiği ekleyin.

## <a name="unity-debugging"></a>Unity hata ayıklaması

Unity projelerinin Mac için Visual Studio hata ayıklaması yapılabilir.

### <a name="start-debugging"></a>Hata ayıklamayı Başlat

Hata ayıklamayı başlatmak için:

1. **oynat** düğmesine tıklayarak Unity 'ye Visual Studio Bağlan veya **Command + Return** ya da **F5** yazın.

   ![Visual Studio içinde oynat ' ı tıklatın](media/using-vsmac-tools-unity-image5.png)

2. Unity 'ye geçin ve oyunu düzenleyicide çalıştırmak için **Yürüt** düğmesine tıklayın.

   ![Unity 'de Yürüt ' e tıklayın](media/using-vsmac-tools-unity-image6.png)

3. oyun, Visual Studio bağlı durumdayken Unity düzenleyicisinde çalışırken, karşılaştığı herhangi bir kesme noktası oyunun yürütülmesini duraklatır ve oyunun Mac için Visual Studio kesme noktasına isabet ettiği kod satırını getirir.

### <a name="stop-debugging"></a>Hata ayıklamayı Durdur

Hata ayıklamayı durdurmak için:

1. Mac için Visual Studio **durdur** düğmesine tıklayın veya **shıft + Command + Return** tuşlarına basın.

   ![Visual Studio Durdur ' a tıklayın](media/using-vsmac-tools-unity-image7.png)

Mac için Visual Studio hata ayıklama hakkında daha fazla bilgi edinmek için bkz. [hata ayıklayıcıyı kullanma](debugging.md).
