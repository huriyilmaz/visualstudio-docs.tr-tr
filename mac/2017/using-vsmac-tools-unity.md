---
title: Unity için Mac Araçları için Visual Studio kullanma
description: Bu kılavuzda, Unity uzantısı için Mac Tools için Visual Studio'nun nasıl kullanılacağı açıklanmaktadır
author: therealjohn
ms.author: johmil
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: d4df59273db1fab8492b36e87e48e0e770072f17
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79303297"
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Unity için Mac Araçları için Visual Studio kullanma

Bu bölümde, Unity'nin tümleştirme ve üretkenlik özellikleri için Mac Tools için Visual Studio'yu nasıl kullanacağınızı ve Unity geliştirme için Mac hata ayıklama için Visual Studio'yu nasıl kullanacağınızı öğreneceksiniz.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Mac için Visual Studio'da Unity komut dosyaları açma

Mac için Visual Studio [Unity için dış komut dosyası editörü olarak ayarlandıktan](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac)sonra, Unity editöründen herhangi bir komut dosyası nın açılması otomatik olarak başlatAcak veya seçilen komut dosyası açık olarak Mac için Visual Studio'ya geçecektir.

Alternatif olarak, Visual Studio for Mac, Unity'deki **Varlıklar** menüsünden **Açık C# Project'i** seçerek kaynak düzenleyicide komut dosyası açılmadan açılabilir.

![C# projesini aç](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Birlik belgelerine erişim

Mac Tools for Unity için Visual Studio, Unity API belgelerine erişmek için bir kısayol içerir. Mac için Visual Studio'dan Unity API belgelerine erişmek için imleci öğrenmek istediğiniz Unity API'nin üzerine yerleştirin ve **komuta + '** tuşuna basın.

## <a name="intellisense-for-unity-messages"></a>Birlik mesajları için IntelliSense
Unity altyapısı, iletileri MonoBehaviour komut dosyasına yayınlayarak geliştiricilerin OnMouseDown, OnTriggerEnter gibi iletilere tepki veren kod lar yazmalarını sağlar. Bunlar temel MonoBehaviour sınıfındasanal yöntemler olmadığından, MonoDevelop gibi bazı IDA'lar Unity iletileri için kod tamamlama işlevinden yoksundur.

Ancak, Visual Studio for Mac Tools for Unity, IntelliSense işlevini Unity iletilerine genişletir. Bu, MonoBehaviour komut dosyasında Unity iletilerinin uygulanmasını kolaylaştırır ve Unity API'yi öğrenmede yardımcı olur. Birlik mesajları için IntelliSense'i kullanmak için:

1. İmleci MonoBehaviour'tan türeyen bir sınıfın gövdesinin içine yeni bir çizgiye yerleştirin.

2. Birleşme iletisinin adını yazmaya baÅ `OnTriggerEnter`lat

3. "**ont**" harfleri yazıldıktan sonra IntelliSense önerilerinin bir listesi görüntülenir.

   ![IntelliSense Kullanma](media/using-vsmac-tools-unity-image2.png)

4. Listedeki seçim üç şekilde değiştirilebilir:

   * **Yukarı** ve **Aşağı** ok tuşları ile.

   * İstenilen öğenin üzerinde fare ile tıklayarak.

   * İstenilen öğenin adını yazmaya devam ederek.

5. IntelliSense, gerekli parametreler de dahil olmak üzere seçili Birlik iletisini ekleyebilir:

   * **Sekme tuşuna**basarak .

   * **İade**tuşuna basarak .

   * Seçili öğeyi çift tıklatarak.

   ![IntelliSense'den Birlik iletisi ekleme](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>Yeni Unity dosyaları ve klasörleri ekleme

Unity düzenleyicisinde bir Unity projesine her zaman yeni dosyalar ekleyebilirsiniz, ancak Visual Studio için Visual Studio'da kolayca yeni Unity komut dosyaları, gölgeleyiciler ve klasörler oluşturmaolanağı sağlar.

### <a name="add-a-new-c-monobehaviour-script"></a>Yeni bir C# MonoBehaviour komut dosyası ekleme

Yeni bir C# MonoBehaviour komut dosyası eklemek için, **Çözüm defterindeki Varlıklar klasörüne** veya alt dizinlerinden birine sağ tıklayın ve **Yeni MonoBehaviour > ekle'yi**seçin.

![Yeni MonoBehavior ekle](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>Yeni bir Unity shader ekleme

Yeni bir Unity shader eklemek için, **Çözüm defterindeki Varlıklar klasörüne** veya bir alt dizine sağ tıklayın ve **Yeni Gölgeli> ekle'yi**seçin.

### <a name="add-a-new-folder"></a>Yeni bir klasör ekleme

Yeni bir klasör eklemek **için, Çözüm defterindeki Varlıklar klasörüne** veya bir alt dizine sağ tıklayın ve **Yeni Klasör > ekle'yi**seçin.

Bu eklemeler Unity düzenleyicisinin Proje penceresinde yansıtılır.

### <a name="to-rename-a-file-or-folder"></a>Bir dosyayı veya klasörü yeniden adlandırmak için
Çözüm defterinde yeniden adlandırmak için öğeye **sağ tıklayın** ve **Yeniden Adlandır'ı seçin...**.

> [!NOTE]
> Komut dosyası olmayan yeni bir Unity projeniz varsa ve Varlıklar klasörü Visual Studio for Mac'teki Solution pad'de görünmüyorsa, Unity düzenleyicisinin içinden bir c# komut dosyası ekleyin.

## <a name="unity-debugging"></a>Birlik hata ayıklama

Unity projeleri Mac için Visual Studio ile debugged olabilir.

### <a name="start-debugging"></a>Hata ayıklama yı başlatma

Hata ayıklamaya başlamak için:

1. **Oynat** düğmesini tıklatarak Visual Studio'yu Birliğe bağlayın veya **Komut + İade**veya **F5**yazın.

   ![Visual Studio'da Oynat'a tıklayın](media/using-vsmac-tools-unity-image5.png)

2. Unity'ye geçin ve oyunu editörde çalıştırmak için **Play** butonuna tıklayın.

   ![Unity Oyna'ya tıklayın](media/using-vsmac-tools-unity-image6.png)

3. Visual Studio'ya bağlıyken unity editöründe oyun çalışırken, karşılaşılan herhangi bir kesme noktası oyunun yürütülmesini duraklatacak ve oyunun Mac için Visual Studio'da kırılma noktasına geldiği kod çizgisini açacaktır.

### <a name="stop-debugging"></a>Hata ayıklamayı durdur

Hata ayıklamayı durdurmak için:

1. Mac için Visual Studio'da **Durdur** düğmesine tıklayın veya **Shift + Command + Return**tuşuna basın.

   ![Visual Studio'da Dur'a tıklayın](media/using-vsmac-tools-unity-image7.png)

Mac için Visual Studio'da hata ayıklama hakkında daha fazla bilgi edinmek için [bkz.](debugging.md)
