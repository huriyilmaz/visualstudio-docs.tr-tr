---
title: Dosyalarda bulma ve değiştirme
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dddd55714e53516ba1ccd8a11c99761a4db7136a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585632"
---
# <a name="replace-in-files"></a>Dosyalarda Değiştir

**Dosyalarda Değiştir,** bir dize veya ifade için belirli bir dosya kümesinin kodunu aramanızı ve bulunan eşleşmelerin bazılarını veya tümünü değiştirmenizi sağlar. Bulunan eşleşmeler ve alınan eylemler **Sonuç seçeneklerinde**seçilen **Sonuçları Bul** penceresinde listelenir.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürüme bağlı olarak **Yardım'da** açıklananlardan farklı olabilir. Ayarlarınızı değiştirmek için, örneğin **Genel** veya **Görsel C++** ayarlarını değiştirmek **için, Araçlar** > **İçe Ve Dışa Aktar Ayarlarını**seçin ve ardından **tüm ayarları sıfırla'yı**seçin.

Bul **ve Değiştir** penceresinde **Dosyalarda Değiştir'i** görüntülemek için aşağıdaki yöntemlerden birini kullanabilirsiniz.

## <a name="to-display-replace-in-files"></a>Dosyalarda Değiştir'i görüntülemek için

1. **Edit** menüsünde **Bul ve Değiştir'i**genişletin.

2. **Dosyalarda Değiştir'i**seçin.

   — veya —

   Bul **ve Değiştir** penceresi zaten açıksa, araç çubuğunda **Dosyalarda Değiştir'i**seçin.

## <a name="find-what"></a>Neyi bul

Yeni bir metin dizesini veya ifadesini aramak için kutuda belirtin. En son aradığınız 20 dizeden herhangi birini aramak için açılır listeyi açın ve dizeyi seçin. Arama dizenizde bir veya daha fazla normal ifade kullanmak istiyorsanız bitişik **İfade Oluşturucu** düğmesini seçin. Daha fazla bilgi için [bkz.](../ide/using-regular-expressions-in-visual-studio.md)

> [!NOTE]
> **İfade Oluşturucu** düğmesi yalnızca **Bul seçenekleri**altında Düzenli **İfadeleri Kullan'ı** seçtiyseniz etkinleştirilir.

## <a name="replace-with"></a>Şununla Değiştir

Hangi kutuyu başka bir dizeyle **bul** dizeörneklerini değiştirmek **Replace With** için, değiştir kutusuna yedek dize girin. **Ne** kutusu bul'daki dize örneklerini silmek için bu alanı boş bırakın. En son aradığınız 20 dizeyi görüntülemek için listeyi açın. Değiştirme dizenizde bir veya daha fazla normal ifade kullanmak istiyorsanız bitişik **İfade Oluşturucu** düğmesini seçin. Daha fazla bilgi için [bkz.](../ide/using-regular-expressions-in-visual-studio.md)

## <a name="look-in"></a>Şuna bak

**Açılan** listeden seçilen seçenek, **Dosyalarda Değiştir'in** yalnızca etkin dosyalarda mı yoksa belirli klasörlerde depolanan tüm dosyaları mı arayacağını belirler. Listeden bir arama kapsamı seçin, klasör yolu yazın veya **Arama Klasörleri Seç** iletişim kutusunu görüntülemek için **Gözat (...)** düğmesini tıklatın ve aramak için bir klasör kümesi seçin. Doğrudan **Bak** kutusuna bir yol da yazabilirsiniz.

> [!NOTE]
> **Seçili Bak** seçeneği, kaynak kodu denetiminden çıkış yaptığınız bir dosyada arama nıza neden oluyorsa, yalnızca yerel makinenize indirilen dosyanın sürümü aranır.

## <a name="find-options"></a>Seçenekleri bul

**Bul seçenekleri** bölümünü genişletebilir veya daraltabilirsiniz. Aşağıdaki seçenekler seçilebilir veya temizlenebilir:

**Durum kılıfını eşleştir**

Seçildiğinde, **Sonuçları Bul** pencereleri yalnızca hem içerikle hem de büyük/küçük harfle eşleşen hangi dizeyi **bul** örneklerini görüntüler. Örneğin, **Match case** ile "MyObject" için yapılan bir arama "MyObject" döndürecek, ancak "myobject" veya "MYOBJECT" değil.

**Tüm kelimeyi eşleştir**

Seçildiğinde, **Sonuçları Bul** pencereleri yalnızca tam sözcüklerle eşleşen **dizesini bul** örneklerini görüntüler. Örneğin, "MyObject" için yapılan bir arama "MyObject" döndürür, ancak "CMyObject" veya "MyObjectC" döndürmez.

**Düzenli İfadeler Kullanma**

Bu onay kutusu seçildiğinde, **ne bul** veya metin **kutularıyla değiştir'deki** metin desenlerini tanımlamak için özel gösterimler kullanabilirsiniz. Bu gösterimlerin bir listesi için visual [studio'da düzenli ifadeleri kullan'a](../ide/using-regular-expressions-in-visual-studio.md)bakın.

**Bu dosya türlerine bakın**

Bu liste, dizinlerde **Bak'ta** aranacak dosya türlerini gösterir. Bu alan boş bırakılırsa, **Görünüm** dizinlerinde bulunan tüm dosyalar aranır. Bu tür dosyaların bulunacağı önceden yapılandırılmış bir arama dizesi girmek için listedeki herhangi bir öğeyi seçin.

## <a name="result-options"></a>Sonuç seçenekleri

**Sonuç seçenekleri** bölümünü genişletebilir veya daraltabilirsiniz. Aşağıdaki seçenekler seçilebilir veya temizlenebilir:

**Sonuçları Bul 1** penceresi

Seçildiğinde, geçerli aramanın sonuçları Sonuçları Bul **1** penceresinin içeriğini değiştirir. Bu pencere, arama sonuçlarınızı görüntülemek için otomatik olarak açılır. Bu pencereyi el ile açmak için **Görünüm** menüsünden **Diğer Windows'u** seçin ve Sonuçları Bul **1'i**seçin.

**Sonuçları Bul 2** penceresi

Seçildiğinde, geçerli aramanın sonuçları Sonuçları Bul **2** penceresinin içeriğinin yerini alır. Bu pencere, arama sonuçlarınızı görüntülemek için otomatik olarak açılır. Bu pencereyi el ile açmak için **Görünüm** menüsünden **Diğer Windows'u** seçin ve Sonuçları Bul **2'yi**seçin.

**Yalnızca dosya adlarını görüntüleme**

Bu onay kutusu seçildiğinde, **Sonuçları Bul** pencereleri arama dizesini içeren tüm dosyaların tam adlarını ve yollarını listeler. Ancak, sonuçlar dize görünür kod satırı içermez. Bu onay kutusu yalnızca **Dosyaları Bul** için kullanılabilir.

**Tümlerini Değiştir'den sonra değiştirilen dosyaları açık tutun**

Seçildiğinde, değişiklikleri geri alabilmeniz veya kaydedebilirsiniz. Bellek kısıtlamaları, değiştirme işleminden sonra açık kalabilecek dosya sayısını sınırlayabilir.

> [!CAUTION]
> Yalnızca düzenleme için açık kalan dosyalarda **Geri Al'ı** kullanabilirsiniz. Bu seçenek seçili değilse, düzenleme için zaten açık olmayan dosyalar kapalı kalır ve bu dosyalarda **Geri Al** seçeneği bulunmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Metin bulma ve değiştirme](../ide/finding-and-replacing-text.md)
- [Dosyalarda bulun](../ide/find-in-files.md)
- [Visual Studio komutları](../ide/reference/visual-studio-commands.md)
