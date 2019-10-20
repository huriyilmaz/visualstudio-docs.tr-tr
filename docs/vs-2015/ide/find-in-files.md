---
title: Dosyalarda bul | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.findinfiles
- vs.findinfiles
helpviewer_keywords:
- objects [Visual Studio], finding
- text searches, replacing text
- objects [Visual Studio], searching for
- Find and Replace window, Find in Files tab
- text searches, Find and Replace window
- documents, searching
- files, searching
- Find in Files tab, Find and Replace window
ms.assetid: 989e0737-46d7-4474-8453-fad52a74669d
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5e21d0880813452e37c9e20afdc98321e4b2e3a6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655895"
---
# <a name="find-in-files"></a>Dosyalarda Bul
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dosyalarda bul * *, belirtilen dosya kümesinde arama yapmanıza olanak tanır. Bulunan eşleşmeler ve gerçekleştirilen eylemler, **sonuç seçeneklerinde**seçilen **sonuçları bul** penceresinde listelenir.

 **Bul ve Değiştir** penceresinde **dosyalarda bul** ' ü göstermek için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz.

### <a name="to-display-find-in-files"></a>Dosyalarda bul ' i görüntüleme

1. Menü çubuğunda **Düzenle**, **Bul ve Değiştir**' i seçin.

2. **Dosyalarda bul '** ı seçin.

   Bir bul işlemini iptal etmek için CTRL + BREAK tuşlarına basın.

> [!NOTE]
> Bul ve Değiştir aracı, `Hidden` veya `System` özniteliği ayarlanmış dizinlerde arama yapmaz.

## <a name="find-what"></a>Neyi bulun
 Yeni bir metin dizesi veya ifade aramak için, kutuyu kutuda belirtin. En son aradığınız 20 dizeden herhangi birini aramak için listeyi açın ve aramak istediğiniz dizeyi seçin. Arama dizenizde bir veya daha fazla normal ifade kullanmak istiyorsanız bitişik **Ifade Oluşturucu** düğmesini seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da normal Ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Arama yeri
 **Arama** açılan listesinden seçilen seçenek, **dosyalarda bul '** un yalnızca şu anda etkin olan dosyalarda mi yoksa belirli klasörlerde depolanan tüm dosyalarda mı arayacağını belirler. Listeden bir arama kapsamı seçin veya **Arama Klasörleri seç** iletişim kutusunu ve kendi dizin kümesini girmek Için, **Araştır (...)** düğmesine tıklayın. Ayrıca, doğrudan **Ara** kutusuna bir yol yazabilirsiniz.

> [!WARNING]
> **Tüm çözüm** veya **geçerli proje** seçenekleri ile proje ve çözüm dosyaları aranmaz. Proje dosyalarına bakmak isterseniz, bir arama klasörü seçin.

> [!NOTE]
> Seçili **Ara** seçeneği, kaynak kodu denetiminden kullanıma aldığınız bir dosyayı aramanıza neden oluyorsa, yalnızca yerel makinenize indirilmiş olan dosyanın bulunduğu dosya aranır.

## <a name="include-subfolders"></a>Alt klasörleri dahil et
 **Arama** klasörü alt klasörlerinin aranacağını belirtir.

## <a name="find-options"></a>Bulma seçenekleri
 **Seçenekleri bul** bölümünü genişletebilir veya daraltabilirsiniz. Aşağıdaki seçenekler seçilebilir veya temizlenemez:

 Seçili olduğunda büyük/küçük harf **Eşleştir arama büyük** /küçük harfe duyarlı olacaktır

 Tüm sözcüğü eşle seçildiğinde, **sonuçları bul** penceresi yalnızca tüm sözcük eşleşmelerini döndürür.

 Normal Ifadeleri kullan bu onay kutusu işaretliyse, **bul** veya **Değiştir** metin kutularında eşleşecek metin desenleri tanımlamak için özel gösterimler kullanabilirsiniz. Bu gösterimlerin bir listesi için bkz. [Visual Studio 'Da normal Ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md).

 Bu dosya türlerine bakın bu liste, dizinde **Bakılacak** dosya türlerini belirtir. Bu alan boşsa, dizinlerde **Ara içindeki** tüm dosyalar aranacaktır.

 Belirli türlerin dosyalarını bulacak önceden yapılandırılmış bir arama dizesi girmek için listedeki herhangi bir öğeyi seçin.

## <a name="result-options"></a>Sonuç seçenekleri
 **Sonuç seçenekleri** bölümünü genişletebilir veya daraltabilirsiniz. Aşağıdaki seçenekler seçilebilir veya temizlenemez:

 Sonuçları Bul 1 penceresi seçildiğinde, geçerli aramanın sonuçları, **sonuçları Bul 1** penceresinin içeriğinin yerini alır. Bu pencere, arama sonuçlarınızı göstermek için otomatik olarak açılır. Bu pencereyi el ile açmak için, **Görünüm** menüsünde **diğer pencereler** ' i seçin ve **sonuçları Bul 1**' i seçin.

 Sonuçları bul 2 penceresini seçtiğinizde, geçerli aramanın sonuçları, **sonuçları bul 2** penceresinin içeriğinin yerini alır. Bu pencere, arama sonuçlarınızı göstermek için otomatik olarak açılır. Bu pencereyi el ile açmak için, **Görünüm** menüsünde **diğer pencereler** ' i seçin ve **sonuçları bul 2**' yi seçin.

 Görüntü dosyası adları yalnızca arama eşleşmelerini içeren dosyaların bir listesini görüntüler.

 Sona Ekle sonuçları, aramanın sonuçlarını önceki arama sonuçlarına ekler.

## <a name="see-also"></a>Ayrıca Bkz.
 [Dosyalardaki metni bulma ve değiştirme](../ide/finding-and-replacing-text.md) [](../ide/replace-in-files.md) [Visual Studio komutları](../ide/reference/visual-studio-commands.md)
