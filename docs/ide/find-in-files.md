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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595481"
---
# <a name="find-in-files"></a>Dosyalarda Bul

**Dosyaları Bul,** belirli bir dosya kümesinde arama yapmanızı sağlar. Bulunan eşleşmeler ve alınan eylemler **Sonuç seçeneklerinde**seçilen **Sonuçları Bul** penceresinde listelenir.

Bul **ve Değiştir** penceresinde **Dosyalarda Bul'u** görüntülemek için aşağıdaki yöntemlerden birini kullanabilirsiniz.

## <a name="to-display-find-in-files"></a>Dosyalarda Bul'u görüntülemek için

1. Menü çubuğunda**Bul ve Değiştir'i** **seç.** > 

1. **Dosyalarda Bul'u**seçin.

Bul işlemini iptal etmek için **Ctrl** + **Break'e**basın.

> [!NOTE]
> Bul ve Değiştir aracı dizinleri `Hidden` veya `System` öznitelik ile arama yapmaz.

## <a name="find-what"></a>Neyi bul

Yeni bir metin dizesini veya ifadesini aramak için kutuda belirtin. En son aradığınız 20 dizeden herhangi birini aramak için açılır listeyi açın ve dizeyi seçin. Arama dizenizde bir veya daha fazla normal ifade kullanmak istiyorsanız bitişik **İfade Oluşturucu** düğmesini seçin. Daha fazla bilgi için bkz. [Visual Studio'da düzenli ifadeleri kullanma.](../ide/using-regular-expressions-in-visual-studio.md)

> [!NOTE]
> **İfade Oluşturucu** düğmesi yalnızca **Bul seçenekleri**altında Düzenli **İfadeleri Kullan'ı** seçtiyseniz etkinleştirilir.

## <a name="look-in"></a>Şuna bak

Açılan listedeki **Bak'tan** seçilen seçenek, **Dosyalarda Bul'un** yalnızca etkin dosyalarda mı yoksa belirli klasörlerde depolanan tüm dosyalarda mı arama dığını belirler. Listeden bir arama kapsamı seçin veya **Arama Klasörleri Seç** iletişim kutusunu görüntülemek ve kendi dizin kümenizi girmek için **Gözat (...)** düğmesini tıklatın. Doğrudan **Bak** kutusuna bir yol da yazabilirsiniz.

> [!WARNING]
> Tüm **Çözüm** veya **Geçerli Proje** seçenekleriyle proje ve çözüm dosyaları aranmaz. Proje dosyalarına bakmak istiyorsanız, bir arama klasörü seçin.

> [!NOTE]
> **Seçili Bak** seçeneği, kaynak kodu denetiminden çıkış yaptığınız bir dosyada arama nıza neden oluyorsa, yalnızca yerel makinenize indirilen dosyanın sürümü aranır.

## <a name="include-subfolders"></a>Alt klasörleri ekleme

**Bak** klasöründeki alt klasörlerin aranacağını belirtir.

## <a name="find-options"></a>Seçenekleri bul

**Bul seçenekleri** bölümünü genişletebilir veya daraltabilirsiniz. Aşağıdaki seçenekler seçilebilir veya temizlenebilir:

**Durum kılıfını eşleştir**

Seçildiğinde, **Sonuçları Bul** araması büyük/küçük harf duyarlı olacaktır

**Tüm kelimeyi eşleştir**

Seçildiğinde, **Sonuçları Bul** pencereleri yalnızca tüm sözcük eşleşmelerini döndürecektir.

**Düzenli İfadeler Kullanma**

Bu onay kutusu seçilirse, **ne bul** veya metin **kutularıile değiştir'de** eşleşecek metin desenlerini tanımlamak için özel gösterimler kullanabilirsiniz. Bu gösterimlerin bir listesi için visual [studio'da düzenli ifadeleri kullanma](../ide/using-regular-expressions-in-visual-studio.md)bölümüne bakın.

**Bu dosya türlerine bakın**

Bu liste, dizinlerde **Bak'ta** aranacak dosya türlerini gösterir. Bu alan boşsa, **Görünüm** dizinlerinde bulunan tüm dosyalar aranır.

Bu tür dosyaların bulunacağı önceden yapılandırılmış bir arama dizesi girmek için listedeki herhangi bir öğeyi seçin.

## <a name="result-options"></a>Sonuç seçenekleri

**Sonuç seçenekleri** bölümünü genişletebilir veya daraltabilirsiniz. Aşağıdaki seçenekler seçilebilir veya temizlenebilir:

**Sonuçları bulma 1 penceresi**

Seçildiğinde, geçerli aramanın sonuçları Sonuçları Bul **1** penceresinin içeriğini değiştirir. Bu pencere, arama sonuçlarınızı görüntülemek için otomatik olarak açılır. Bu pencereyi el ile açmak için **Görünüm** menüsünden **Diğer Windows'u** seçin ve Sonuçları Bul **1'i**seçin.

**Sonuçları bulma 2 penceresi**

Seçildiğinde, geçerli aramanın sonuçları Sonuçları Bul **2** penceresinin içeriğinin yerini alır. Bu pencere, arama sonuçlarınızı görüntülemek için otomatik olarak açılır. Bu pencereyi el ile açmak için **Görünüm** menüsünden **Diğer Windows'u** seçin ve Sonuçları Bul **2'yi**seçin.

**Yalnızca dosya adlarını görüntüleme**

Arama eşleşmelerini görüntülemek yerine arama eşleşmeleri içeren dosyaların listesini görüntüler.

**Sonuçları ekle**

Aramasonuçları önceki arama sonuçlarına ekler.

## <a name="see-also"></a>Ayrıca bkz.

- [Metni bulma ve değiştirme](../ide/finding-and-replacing-text.md)
- [Dosyalarda Değiştir](../ide/replace-in-files.md)
- [Visual Studio komutları](../ide/reference/visual-studio-commands.md)
