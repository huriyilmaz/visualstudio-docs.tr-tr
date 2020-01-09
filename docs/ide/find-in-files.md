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
ms.openlocfilehash: 5e1f067df647f843819e085f283005606699f3bb
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595481"
---
# <a name="find-in-files"></a>Dosyalarda Bul

**Dosyalarda bul** , belirtilen dosya kümesinde arama yapmanıza olanak tanır. Eşleşme bulundu ve gerçekleştirilen eylemler listelenen **sonuçları Bul** seçili penceresi **neden seçenekleri**.

**Bul ve Değiştir** penceresinde **dosyalarda bul** ' ü göstermek için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz.

## <a name="to-display-find-in-files"></a>Dosyalarda bul ' i görüntüleme

1. Menü çubuğunda **düzenle** > **Bul ve Değiştir**' i seçin.

1. **Dosyalarda bul '** ı seçin.

Bir bul işlemini iptal etmek için **Ctrl** + **Break**tuşlarına basın.

> [!NOTE]
> Bul ve Değiştir aracı Dizin `Hidden` veya `System` özniteliğiyle arama yapmaz.

## <a name="find-what"></a>Sonrakini Bul

Yeni metin dizesi veya ifadesi için arama yapmak için kutuya belirtin. Herhangi biri için en son Aranan 20 dizeleri aramak için açılan listeyi açın ve dize seçin. Bitişik seçin **ifade oluşturucu** bir veya daha fazla normal ifadeler, arama dizesinde kullanmak istiyorsanız düğmesi. Daha fazla bilgi için bkz. [Visual Studio 'da normal Ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> **İfade oluşturucu** düğmesi etkinleştirilecektir seçtiyseniz **normal ifadeler kullanmanız** altında **bulma seçeneklerini**.

## <a name="look-in"></a>Bakılacak konum

**Arama** açılan listesinden seçilen seçenek, **dosyalarda bul '** un yalnızca şu anda etkin olan dosyalarda mi yoksa belirli klasörlerde depolanan tüm dosyalarda mı arayacağını belirler. Listeden bir arama kapsamı seçin veya **Arama Klasörleri seç** iletişim kutusunu ve kendi dizin kümesini girmek Için, **Araştır (...)** düğmesine tıklayın. Doğrudan bir yolu da yazabilirsiniz **konum** kutusu.

> [!WARNING]
> **Tüm çözüm** veya **geçerli proje** seçenekleri ile proje ve çözüm dosyaları aranmaz. Proje dosyalarına bakmak isterseniz, bir arama klasörü seçin.

> [!NOTE]
> Varsa **konum** seçeneğe kullanıma kaynak kod denetiminden yalnızca yerel makinenize indirilen dosyanın sürüm aranır dosya arama neden olur.

## <a name="include-subfolders"></a>Alt klasörleri dahil et

**Arama** klasörü alt klasörlerinin aranacağını belirtir.

## <a name="find-options"></a>Bulma seçenekleri

Genişlet veya daralt **bulma seçeneklerini** bölümü. Aşağıdaki seçenekler seçilen veya temizlenen:

**Büyük küçük harf duyarlı**

Seçildiğinde, bir **bul sonucu** arama büyük/küçük harfe duyarlı olacaktır

**Bütün kelimeyi eşleştir**

Seçildiğinde, **sonuçları bul** penceresi yalnızca tüm sözcük eşleşmelerini döndürür.

**Normal İfadeler Kullanma**

Bu onay kutusu işaretliyse, **bulma** veya **değiştirme** metin kutularında eşleşmek üzere metin desenleri tanımlamak için özel gösterimler kullanabilirsiniz. Bu gösterimlerin bir listesi için bkz. [Visual Studio 'da normal Ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md).

**Bu dosya türlerini Ara**

Bu liste içinde arama yapmak dosya türlerini gösterir **konum** dizinleri. Bu alan boşsa, dizinlerde **Ara içindeki** tüm dosyalar aranacaktır.

Listede bu belirli türlerin dosyaları bulursunuz bir önceden yapılandırılmış bir arama dizesi girin herhangi bir öğeyi seçin.

## <a name="result-options"></a>Sonuç seçenekleri

Genişlet veya daralt **neden seçenekleri** bölümü. Aşağıdaki seçenekler seçilen veya temizlenen:

**Arama sonuçları 1 penceresi**

Bu onay kutusu seçildiğinde, geçerli arama sonuçları içeriğini değiştirin **Bul sonuçları 1** penceresi. Bu pencere, arama sonuçlarını görüntülemek için otomatik olarak açılır. El ile bu pencereyi açmak için seçmeniz **diğer Windows** gelen **görünümü** menü ve **Bul sonuçları 1**.

**Sonuçları bul 2 penceresi**

Bu onay kutusu seçildiğinde, geçerli arama sonuçları içeriğini değiştirin **Bul sonuçları 2** penceresi. Bu pencere, arama sonuçlarını görüntülemek için otomatik olarak açılır. El ile bu pencereyi açmak için seçmeniz **diğer Windows** gelen **görünümü** menü ve **Bul sonuçları 2**.

**Sadece dosya adlarını görüntüler**

Arama eşleşmeleri içeren dosyaların bir listesini görüntüler.

**Sonuçları sona Ekle**

Aramadan sonuçları önceki arama sonuçlarına ekler.

## <a name="see-also"></a>Ayrıca bkz.

- [Metni bulma ve değiştirme](../ide/finding-and-replacing-text.md)
- [Dosyalarda Değiştir](../ide/replace-in-files.md)
- [Visual Studio komutları](../ide/reference/visual-studio-commands.md)
