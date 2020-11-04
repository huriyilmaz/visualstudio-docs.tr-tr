---
title: Dosyalarda Bul
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a32720475bda124c563d45133028f43b4f1b9cd
ms.sourcegitcommit: e132a870ec198fdcec289227f1a0c1c48fef070c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93344513"
---
# <a name="find-in-files"></a>Dosyalarda Bul

**Dosyalarda bul** , belirtilen dosya kümesinde arama yapmanıza olanak tanır. Bulunan eşleşmeler ve gerçekleştirilen eylemler, **sonuç seçeneklerinde** seçilen **sonuçları bul** penceresinde listelenir.

**Bul ve Değiştir** penceresinde **dosyalarda bul** ' ü göstermek için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz.

## <a name="to-display-find-in-files"></a>Dosyalarda bul ' i görüntüleme

1. Menü çubuğunda **Düzenle**  >  **Bul ve Değiştir** ' i seçin.

1. **Dosyalarda bul '** ı seçin.

Bir bul işlemini iptal etmek için **CTRL**  +  **Kes** ' e basın.

> [!NOTE]
> Bul ve Değiştir aracı, `Hidden` veya özniteliğiyle Dizin aramaz `System` .

## <a name="find-what"></a>Neyi bulun

Yeni bir metin dizesi veya ifade aramak için, kutuyu kutuda belirtin. En son aradığınız 20 dizeden herhangi birini aramak için, açılan listeyi açın ve dizeyi seçin. Arama dizenizde bir veya daha fazla normal ifade kullanmak istiyorsanız bitişik **Ifade Oluşturucu** düğmesini seçin. Daha fazla bilgi için bkz. [Visual Studio 'da normal Ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> **Ifade Oluşturucu** düğmesi yalnızca **Bul seçenekleri** altında **Normal ifadeleri kullan** seçeneğini belirlediyseniz etkinleştirilir.

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

**Büyük/küçük harf eşleştir**

Seçildiğinde, bir **bul sonucu** arama büyük/küçük harfe duyarlı olacaktır

**Sözcüğün tamamını Eşleştir**

Seçildiğinde, **sonuçları bul** penceresi yalnızca tüm sözcük eşleşmelerini döndürür.

**Normal Ifadeleri kullanma**

Bu onay kutusu işaretliyse, **bulma** veya **değiştirme** metin kutularında eşleşmek üzere metin desenleri tanımlamak için özel gösterimler kullanabilirsiniz. Bu gösterimlerin bir listesi için bkz. [Visual Studio 'da normal Ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md).

**Bu dosya türlerine bakın**

Bu liste, dizinde **Bakılacak** dosya türlerini gösterir. Bu alan boşsa, dizinlerde **Ara içindeki** tüm dosyalar aranacaktır.

Belirli türlerin dosyalarını bulacak önceden yapılandırılmış bir arama dizesi girmek için listedeki herhangi bir öğeyi seçin.

## <a name="result-options"></a>Sonuç seçenekleri

**Sonuç seçenekleri** bölümünü genişletebilir veya daraltabilirsiniz. Aşağıdaki seçenekler seçilebilir veya temizlenemez:

**Arama sonuçları 1 penceresi**

Seçildiğinde, geçerli aramanın sonuçları, **sonuçları Bul 1** penceresinin içeriğinin yerini alır. Bu pencere, arama sonuçlarınızı göstermek için otomatik olarak açılır. Bu pencereyi el ile açmak için, **Görünüm** menüsünde **diğer pencereler** ' i seçin ve **sonuçları Bul 1** ' i seçin.

**Sonuçları bul 2 penceresi**

Seçildiğinde, geçerli aramanın sonuçları, **bulma sonuçları 2** penceresinin içeriğinin yerini alır. Bu pencere, arama sonuçlarınızı göstermek için otomatik olarak açılır. Bu pencereyi el ile açmak için, **Görünüm** menüsünde **diğer pencereler** ' i seçin ve **sonuçları bul 2** ' yi seçin.

**Yalnızca dosya adlarını görüntüle**

Arama eşleşmeleri içeren dosyaların bir listesini görüntüler.

**Sonuçları sona Ekle**

Aramadan sonuçları önceki arama sonuçlarına ekler.

## <a name="see-also"></a>Ayrıca bkz.

- [Metni bulma ve değiştirme](../ide/finding-and-replacing-text.md)
- [Dosyalarda Değiştir](../ide/replace-in-files.md)
- [Visual Studio komutları](../ide/reference/visual-studio-commands.md)