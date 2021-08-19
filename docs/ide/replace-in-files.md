---
title: Dosyalarda bul ve Değiştir
description: Dosyaları değiştirme özelliği hakkında bilgi edinin ve bir dize veya ifade için belirtilen dosya kümesinin kodunu aramanıza ve bulunan eşleşmelerin bazılarını veya tümünü değiştirmenize nasıl izin verdiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- find and replace
- replace in files
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: cd651db796bcf4e6d626a6cc348a25f5a7f80794
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143462"
---
# <a name="replace-in-files"></a>Dosyalarda Değiştir

**Dosyalardaki Değiştir** bir dize veya ifade için belirtilen dosya kümesinin kodunu aramanıza ve bulunan eşleşmelerin bazılarını veya tümünü değiştirmenize izin verir. Bulunan eşleşmeler ve gerçekleştirilen eylemler, **sonuç seçeneklerinde** seçilen **sonuçları bul** penceresinde listelenir.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümüne bağlı olarak **Yardım** bölümünde açıklananlardan farklı bir durum içerebilir. ayarlarınızı değiştirmek (örneğin, **genel** veya **Visual C++** ayarları) için **araçlar**  >  **içeri aktar ve dışarı aktar Ayarlar**' ı seçin ve ardından **tüm ayarları sıfırla**' yı seçin.

**Bul ve Değiştir** penceresindeki **dosyalardaki değiştirme** 'yi göstermek için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz.

## <a name="to-display-replace-in-files"></a>Dosyaların değiştirilmesini görüntüleme

1. **Düzenle** menüsünde **Bul ve Değiştir**' i genişletin.

2. **Dosyalarda Değiştir '** i seçin.

   veya

   **Bul ve Değiştir** penceresi zaten açıksa, araç çubuğunda, **dosyalarda Değiştir**' i seçin.

## <a name="find-what"></a>Neyi bulun

Yeni bir metin dizesi veya ifade aramak için, kutuyu kutuda belirtin. En son aradığınız 20 dizeden herhangi birini aramak için, açılan listeyi açın ve dizeyi seçin. Arama dizenizde bir veya daha fazla normal ifade kullanmak istiyorsanız bitişik **Ifade Oluşturucu** düğmesini seçin. Daha fazla bilgi için bkz. [Visual Studio normal Ifadeleri kullanma](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> **Ifade Oluşturucu** düğmesi yalnızca **Bul seçenekleri** altında **Normal ifadeleri kullan** seçeneğini belirlediyseniz etkinleştirilir.

## <a name="replace-with"></a>Şununla Değiştir

**Bulunacak** kutusunda bulunan dize örneklerini başka bir dizeyle değiştirmek Için, **Değiştir** kutusuna değiştirme dizesini girin. **Bulunacak** kutusunda dize örneklerini silmek için bu alanı boş bırakın. En son aradığınız 20 dizeyi göstermek için listeyi açın. Değiştirme dizenizde bir veya daha fazla normal ifade kullanmak istiyorsanız bitişik **Ifade Oluşturucu** düğmesini seçin. Daha fazla bilgi için bkz. [Visual Studio normal Ifadeleri kullanma](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Arama yeri

**Içinde ara** açılan listesinden seçilen seçenek, **dosyalardaki Değiştir** 'in yalnızca şu anda etkin dosyalardaki arama yapıp kullanmadığını veya belirli klasörler içinde depolanan tüm dosyaları arayacağını belirler. Listeden bir arama kapsamı seçin, bir klasör yolu yazın veya arama **Klasörleri seç** iletişim kutusunu göstermek için Araştır **(...)** düğmesine tıklayın ve aranacak bir klasör kümesi seçin. Ayrıca, doğrudan **Ara** kutusuna bir yol yazabilirsiniz.

> [!NOTE]
> Seçili **Ara** seçeneği, kaynak kodu denetiminden kullanıma aldığınız bir dosyayı aramanıza neden oluyorsa, yalnızca yerel makinenize indirilmiş olan dosyanın bulunduğu dosya aranır.

## <a name="find-options"></a>Bulma seçenekleri

**Seçenekleri bul** bölümünü genişletebilir veya daraltabilirsiniz. Aşağıdaki seçenekler seçilebilir veya temizlenemez:

**Büyük/küçük harf eşleştir**

Seçildiğinde, **sonuçları bul** penceresi yalnızca içeriğe ve büyük/küçük harflere göre eşleşen dize **bulma** örnekleri görüntülenir. Örneğin, **eşleşme durumu** seçiliyken "MyObject" araması "MyObject" döndürür ancak "MyObject" veya "MyObject" olarak değil.

**Sözcüğün tamamını Eşleştir**

Seçildiğinde, **sonuçları bul** penceresi yalnızca, tüm sözcüklerde eşleşen dizeyi **bul** örnekleri görüntülenir. Örneğin, "MyObject" araması "MyObject" döndürür ancak "CMyObject" veya "MyObjectC" olarak değil.

**Normal Ifadeleri kullanma**

Bu onay kutusu seçildiğinde, **bul** veya **Değiştir** metin kutularında metin desenleri tanımlamak için özel gösterimler kullanabilirsiniz. Bu gösterimlerin bir listesi için bkz. [Visual Studio normal Ifadeleri kullanma](../ide/using-regular-expressions-in-visual-studio.md).

**Bu dosya türlerine bakın**

Bu liste, dizinde **Bakılacak** dosya türlerini gösterir. Bu alan boş bırakılırsa, dizinlerde **Bakılacak** tüm dosyalar aranır. Belirli türlerin dosyalarını bulacak önceden yapılandırılmış bir arama dizesi girmek için listedeki herhangi bir öğeyi seçin.

## <a name="result-options"></a>Sonuç seçenekleri

**Sonuç seçenekleri** bölümünü genişletebilir veya daraltabilirsiniz. Aşağıdaki seçenekler seçilebilir veya temizlenemez:

**Arama sonuçları 1** penceresi

Seçildiğinde, geçerli aramanın sonuçları, **sonuçları Bul 1** penceresinin içeriğinin yerini alır. Bu pencere, arama sonuçlarınızı göstermek için otomatik olarak açılır. bu pencereyi el ile açmak için, **görünüm** menüsünden **diğer Windows** ' yi seçin ve **sonuçları bul 1**' i seçin.

**Sonuçları bul 2** penceresi

Seçildiğinde, geçerli aramanın sonuçları, **bulma sonuçları 2** penceresinin içeriğinin yerini alır. Bu pencere, arama sonuçlarınızı göstermek için otomatik olarak açılır. bu pencereyi el ile açmak için, **görünüm** menüsünden **diğer Windows** ' yi seçin ve **sonuçları bul 2**' yi seçin.

**Yalnızca dosya adlarını görüntüle**

Bu onay kutusu seçildiğinde, **sonuçları bul** penceresi, arama dizesini içeren tüm dosyalar için tam adları ve yolları listeler. Ancak sonuçlar, dizenin göründüğü kod satırını içermez. Bu onay kutusu yalnızca **dosyalarda bul** için kullanılabilir.

**Tümünü değiştirdikten sonra değiştirilen dosyaları açık tut**

Seçildiğinde, değişiklikleri geri alabilir veya kaydedebilirsiniz. bu sayede değişiklikleri geri alabilir veya kaydedebilirsiniz. Bellek kısıtlamaları, bir değiştirme işleminden sonra açık kalabilecek dosya sayısını sınırlayabilir.

> [!CAUTION]
> Yalnızca düzenlenmek üzere açık kalan dosyalar üzerinde **geri al** ' i kullanabilirsiniz. Bu seçenek seçilmezse, zaten düzenlenmek üzere açık olmayan dosyalar kapalı kalır ve bu dosyalarda **geri alma** seçeneği kullanılabilir olmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Metin bulma ve değiştirme](../ide/finding-and-replacing-text.md)
- [Dosyalarda bul](../ide/find-in-files.md)
- [Visual Studio komutları](../ide/reference/visual-studio-commands.md)
