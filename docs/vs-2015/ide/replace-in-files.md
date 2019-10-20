---
title: Dosyalarda Değiştir | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- Find and Replace window, Replace in Files tab
- Replace in Files tab, Find and Replace window
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 001f1faa969275788b10bc9bd1e6398373a54b37
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669969"
---
# <a name="replace-in-files"></a>Dosyalarda Değiştir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dosyalarda Değiştir * * bir dize veya ifade için belirtilen dosya kümesinin kodunu aramanıza ve bulunan eşleşmelerin bazılarını veya tümünü değiştirmenize izin verir. Bulunan eşleşmeler ve gerçekleştirilen eylemler, **sonuç seçeneklerinde**seçilen **sonuçları bul** penceresinde listelenir.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünden Içeri ve dışarı aktarma ayarları ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 **Bul ve Değiştir** penceresindeki **dosyalardaki değiştirme** 'yi göstermek için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz.

### <a name="to-display-replace-in-files"></a>Dosyaların değiştirilmesini görüntüleme

1. **Düzenle** menüsünde **Bul ve Değiştir**' i genişletin.

2. **Dosyalarda Değiştir '** i seçin.

     veya

     **Bul ve Değiştir** penceresi zaten açıksa, araç çubuğunda, **dosyalarda Değiştir**' i seçin.

## <a name="find-what"></a>Neyi bulun
 Yeni bir metin dizesi veya ifade aramak için, kutuyu kutuda belirtin. En son aradığınız 20 dizeden herhangi birini aramak için listeyi açın ve aramak istediğiniz dizeyi seçin. Arama dizenizde bir veya daha fazla normal ifade kullanmak istiyorsanız bitişik **Ifade Oluşturucu** düğmesini seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da normal Ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="replace-with"></a>Değiştir
 **Bulunacak** kutusunda bulunan dize örneklerini başka bir dizeyle değiştirmek Için, **Değiştir** kutusuna değiştirme dizesini girin. **Bulunacak** kutusunda dize örneklerini silmek için bu alanı boş bırakın. En son aradığınız 20 dizeyi göstermek için listeyi açın. Değiştirme dizenizde bir veya daha fazla normal ifade kullanmak istiyorsanız bitişik **Ifade Oluşturucu** düğmesini seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da normal Ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Arama yeri
 **Içinde ara** açılan listesinden seçilen seçenek, **dosyalardaki Değiştir** 'in yalnızca şu anda etkin dosyalardaki arama yapıp kullanmadığını veya belirli klasörler içinde depolanan tüm dosyaları arayacağını belirler. Listeden bir arama kapsamı seçin, bir klasör yolu yazın veya arama **Klasörleri seç** iletişim kutusunu göstermek için Araştır **(...)** düğmesine tıklayın ve aranacak bir klasör kümesi seçin. Ayrıca, doğrudan **Ara** kutusuna bir yol yazabilirsiniz.

> [!NOTE]
> Seçili **Ara** seçeneği, kaynak kodu denetiminden kullanıma aldığınız bir dosyayı aramanıza neden oluyorsa, yalnızca yerel makinenize indirilmiş olan dosyanın bulunduğu dosya aranır.

## <a name="find-options"></a>Bulma seçenekleri
 **Seçenekleri bul** bölümünü genişletebilir veya daraltabilirsiniz. Aşağıdaki seçenekler seçilebilir veya temizlenemez:

 Büyük/küçük harf eşleştir seçilirse, **sonuçları bul** penceresi yalnızca içeriğe ve büyük/küçük harflere göre eşleşen dize **bulma** örnekleri görüntülenir. Örneğin, **eşleşme durumu** seçiliyken "MyObject" araması "MyObject" döndürür ancak "MyObject" veya "MyObject" olarak değil.

 Tüm sözcüğü eşle seçildiğinde, **sonuçları bul** penceresi yalnızca tam sözcüklerde eşleşen dizeyi **bul** örnekleri görüntülenir. Örneğin, "MyObject" araması "MyObject" döndürür ancak "CMyObject" veya "MyObjectC" olarak değil.

 Normal Ifadeleri kullan bu onay kutusu seçildiğinde, **bulma** veya **değiştirme** metin kutularında metin desenleri tanımlamak için özel gösterimler kullanabilirsiniz. Bu gösterimlerin bir listesi için bkz. [Visual Studio 'Da normal Ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md).

 Bu dosya türlerine bakın bu liste, dizinde **Bakılacak** dosya türlerini belirtir. Bu alan boş bırakılırsa, dizinlerde **Bakılacak** tüm dosyalar aranır.

 Belirli türlerin dosyalarını bulacak önceden yapılandırılmış bir arama dizesi girmek için listedeki herhangi bir öğeyi seçin.

## <a name="result-options"></a>Sonuç seçenekleri
 **Sonuç seçenekleri** bölümünü genişletebilir veya daraltabilirsiniz. Aşağıdaki seçenekler seçilebilir veya temizlenemez:

 Sonuçları Bul 1 penceresi seçildiğinde, geçerli aramanın sonuçları, **sonuçları Bul 1** penceresinin içeriğinin yerini alır. Bu pencere, arama sonuçlarınızı göstermek için otomatik olarak açılır. Bu pencereyi el ile açmak için, **Görünüm** menüsünde **diğer pencereler** ' i seçin ve **sonuçları Bul 1**' i seçin.

 Sonuçları bul 2 penceresini seçtiğinizde, geçerli aramanın sonuçları, **sonuçları bul 2** penceresinin içeriğinin yerini alır. Bu pencere, arama sonuçlarınızı göstermek için otomatik olarak açılır. Bu pencereyi el ile açmak için, **Görünüm** menüsünde **diğer pencereler** ' i seçin ve **sonuçları bul 2**' yi seçin.

 Yalnızca bu onay kutusu seçildiğinde dosya adlarını görüntüle Windows 'u Bul penceresi, arama dizesini içeren tüm dosyalar için tam adları ve yolları listeler. Ancak sonuçlar, dizenin göründüğü kod satırını içermez. Bu onay kutusu yalnızca dosyalarda bul için kullanılabilir.

 Tüm seçili olduğunda değiştirilen dosyaları açık tut, tüm değişiklikleri açık halde bırakır, böylece değişiklikleri geri alabilir veya kaydedebilirsiniz. Bellek kısıtlamaları, bir değiştirme işleminden sonra açık kalabilecek dosya sayısını sınırlayabilir.

> [!CAUTION]
> Yalnızca düzenlenmek üzere açık kalan dosyalar üzerinde **geri al** ' i kullanabilirsiniz. Bu seçenek seçilmezse, zaten düzenlenmek üzere açık olmayan dosyalar kapalı kalır ve bu dosyalarda **geri alma** seçeneği kullanılabilir olmaz.

## <a name="see-also"></a>Ayrıca Bkz.
 [Dosyalarda metin bulmayı](../ide/find-in-files.md) [bulma ve değiştirme](../ide/finding-and-replacing-text.md) [Visual Studio komutları](../ide/reference/visual-studio-commands.md)
