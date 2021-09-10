---
title: Unity Mac için Visual Studio Araçları Kullanma
description: Bu kılavuzda Unity uzantısı için Mac için Visual Studio Araçları'nın nasıl kullanacağız?
author: therealjohn
ms.author: johmil
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: d4df59273db1fab8492b36e87e48e0e770072f17
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123962162"
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Unity Mac için Visual Studio Araçları Kullanma

Bu bölümde, Unity'nin tümleştirme ve üretkenlik özellikleri için Mac için Visual Studio Araçları'nın nasıl ve Unity geliştirmesi için Mac için Visual Studio hata ayıklayıcısını kullanmayı öğrenirsiniz.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Unity betiklerini Mac için Visual Studio

Bu Mac için Visual Studio [Unity için](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac)dış betik düzenleyicisi olarak ayarlanırsa, Unity düzenleyicisinden herhangi bir betiğin açılması otomatik olarak başlatılır veya seçilen betik açık Mac için Visual Studio geçiş yapılır.

Alternatif olarak Mac için Visual Studio Unity'de Varlıklar menüsünden C# Project aç'ı seçerek kaynak **düzenleyicide betik** açık değilken de açılabilir. 

![C# projesini açma](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Unity belgelerine erişim

Mac için Visual Studio Unity araçları, Unity API belgelerine erişmek için bir kısayol içerir. Mac için Visual Studio'den Unity API belgelerine erişmek için imleci öğrenmek istediğiniz Unity API'sini üzerine yerleştirerek **+ ' ⌘ tuşlarına basın.**

## <a name="intellisense-for-unity-messages"></a>Unity iletileri için IntelliSense
Unity altyapısı iletileri MonoBehaviour betiklerine yayınlar ve geliştiricilerin OnMouseDown, OnTriggerEnter gibi iletilere tepki veren kodlar yazmasına olanak sağlar. Bunlar temel MonoBehaviour sınıfındaki sanal yöntemler olmadığı için MonoDevelop gibi bazı IDE'ler Unity iletileri için kod tamamlama işlevine sahip değildir.

Ancak, Mac için Visual Studio Araçları, IntelliSense işlevselliğini Unity iletilerine genişlettir. Bu, MonoBehaviour betikleri içinde Unity iletilerinin uygulanmasını kolaylaştırır ve Unity API'sini öğrenme konusunda yardımcı olur. Unity iletileri için IntelliSense kullanmak için:

1. İmleci MonoBehaviour'dan türeten bir sınıfın gövdesinin içindeki yeni bir satıra yerleştirin.

2. Gibi bir Unity iletinin adını yazmaya `OnTriggerEnter` başlayın.

3. **"ont**" harfleri yazıldıktan sonra IntelliSense önerilerinin listesi görüntülenir.

   ![IntelliSense Kullanma](media/using-vsmac-tools-unity-image2.png)

4. Liste seçimi üç şekilde değiştirilebilir:

   * Yukarı **ve Aşağı** **ok tuşlarıyla.**

   * fareyle istenen öğenin üzerine tıklayarak.

   * İstenen öğenin adını yazarak.

5. IntelliSense, gerekli parametreler de dahil olmak üzere seçili Unity iletiyi ekler:

   * Sekme tuşuna **basarak.**

   * Return tuşuna **basarak.**

   * Seçilen öğeye çift tıklayarak.

   ![IntelliSense'den Unity iletisi ekleme](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>Yeni Unity dosyaları ve klasörleri ekleme

Unity düzenleyicisinde bir Unity projesine her zaman yeni dosyalar ekleyebiliyorsanız Mac için Visual Studio kolayca yeni Unity betikleri, gölgelendiriciler ve klasörler oluşturmanıza olanak Visual Studio.

### <a name="add-a-new-c-monobehaviour-script"></a>Yeni bir C# MonoBehaviour betiği ekleme

Yeni bir C# MonoBehaviour betiği eklemek için, Çözüm panelinin **Assets** klasörüne veya alt dizinlerinden birine sağ tıklayın ve Yeni **MonoBehaviour'a >'yi seçin.**

![Yeni MonoBehaviour ekleme](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>Yeni bir Unity gölgelendiricisi ekleme

Yeni bir Unity gölgelendiricisi eklemek için, Çözüm panelinin **Assets** klasörüne veya alt dizinine sağ tıklayın ve Yeni **Gölgelendiriciye Ekle'> seçin.**

### <a name="add-a-new-folder"></a>Yeni klasör ekleme

Yeni klasör eklemek için Çözüm **panelinin Assets** klasörüne veya alt dizinine sağ tıklayın ve Yeni Klasöre **Ekle'> seçin.**

Bu eklemeler Unity düzenleyicisinin Project penceresinde yansıtıldı.

### <a name="to-rename-a-file-or-folder"></a>Bir dosyayı veya klasörü yeniden adlandırmak için
**Çözüm panelinin yeniden** adlandırmak için öğeye sağ tıklayın ve Yeniden **Adlandır... öğesini seçin.**

> [!NOTE]
> Betikleri olan yeni bir Unity projeniz varsa ve Assets klasörü Mac için Visual Studio Çözüm paneli içinde göster yoksa, Unity düzenleyicisinden bir ilk C# betiği ekleyin.

## <a name="unity-debugging"></a>Unity hata ayıklama

Unity projelerinde hata ayıklaması Mac için Visual Studio.

### <a name="start-debugging"></a>Hata ayıklamayı başlatma

Hata ayıklamayı başlatmak için:

1. Bağlan Visual Studio Düğmesine tıklayarak **Unity'ye** tıklayın veya Komut **+ Dönüş veya** **F5 yazın.**

   ![Dosyada Oynat'a Visual Studio](media/using-vsmac-tools-unity-image5.png)

2. Unity'ye geçiş ve **Oynat** düğmesine tıklayarak oyunu düzenleyicide çalıştırın.

   ![Unity'de Oynat'a tıklayın](media/using-vsmac-tools-unity-image6.png)

3. oyun Visual Studio'a bağlıyken Unity düzenleyicisinde çalışırken, karşılaşılan tüm kesme noktaları oyunun yürütülmesini duraklatacak ve oyunun kesme noktasıyla karşılaştığı kod hattını Mac için Visual Studio.

### <a name="stop-debugging"></a>Hata ayıklamayı durdurma

Hata ayıklamayı durdurmak için:

1. Mac için Visual Studio'da Durdur düğmesine tıklayın veya **Shift + Komut + Return tuşlarına basın.** 

   ![Dosyada Durdur'a Visual Studio](media/using-vsmac-tools-unity-image7.png)

Uygulama içinde hata ayıklama hakkında daha fazla Mac için Visual Studio için [bkz. Hata ayıklayıcıyı kullanma.](debugging.md)
