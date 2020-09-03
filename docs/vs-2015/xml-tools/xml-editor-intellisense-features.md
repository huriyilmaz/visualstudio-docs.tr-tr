---
title: XML Düzenleyicisi IntelliSense özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9cd10f9eb0e2899394788c3b19348892837426db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669461"
---
# <a name="xml-editor-intellisense-features"></a>XML Düzenleyicisi IntelliSense Özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML Düzenleyicisi, Visual Studio 'da sağlanan diğer dil düzenleyicilerle karşılaştırılabilir tam IntelliSense özellikleri sağlar. Bu bölümde, IntelliSense 'i XML şeması tanım dili (XSD) ve XSLT belgeleriyle nasıl kullanabileceğiniz açıklanmaktadır.

## <a name="intellisense-in-an-xsd-document"></a>XSD belgesinde IntelliSense
 Bir şema belgeyle ilişkilendirildikten sonra, her yazdığınızda beklenen öğelerin açılan listesini alır `"<"` veya XML Düzenleyicisi araç çubuğundaki bir **nesne üye listesini görüntüle** düğmesine tıklayabilirsiniz. Şemaları XML belgeleriyle ilişkilendirme hakkında daha fazla bilgi için bkz. [XML belge doğrulaması](../xml-tools/xml-document-validation.md).

 Başlangıç etiketinin içinden boşluk yazdığınızda, geçerli öğeye eklenebilen tüm öznitelikleri gösteren bir açılan liste da alırsınız.

 `"="`Bir öznitelik değeri veya değer için açılış tırnak işareti yazdığınızda, bu öznitelik için olası değerlerin listesini de alırsınız. Değerler yalnızca şema, modellerle numaralandırılmış değerler sağlıyorsa `xsd:enumeration` veya öznitelik bir tür ise sağlanır `Boolean` . Veya ' den türetilen bir IntelliSense, bilinen dil kodlarının bir listesi için de sağlanır `xml:lang` `simpleType` `xsd:language` . Bilinen değerlerin IntelliSense listesi `targetNamespace` , ad alanı bildirimleri için verilmiştir.

 Bir IntelliSense, `">"` öğe bir ise başlangıç etiketini kapatmak için yazdığınızda, olası değerlerin bir IntelliSense listesi de sağlanır `simpleType` . Öğelerin davranışı, önceki paragrafta açıklanan özniteliklerin davranışına benzerdir.

 Araç Ipuçları, bu IntelliSense listelerinde `xsd:annotation` `xsd:documentation` , ilişkili şemada bulunan ve bulunan bilgiler temelinde de görüntülenir.

## <a name="intellisense-in-an-xslt-document"></a>XSLT belgesinde IntelliSense
 XSLT belgenize adlandırılmış bir şablon veya öznitelik ekledikten sonra, aşağıdakini eklemek için IntelliSense 'i kullanabilirsiniz:

- Öznitelik kümesi adları.

- Şablon modları.

- Şablon adları.

- Belirli bir mod için parametre adları.

- Belirli bir adlandırılmış şablon için parametre adları.

  Daha fazla bilgi için bkz. [Izlenecek yol: XSLT IntelliSense 'ı kullanma](../xml-tools/walkthrough-using-xslt-intellisense.md) konusu.

## <a name="auto-completion"></a>Otomatik tamamlama
 XML Düzenleyicisi, sizin için gerekli XML söz dizimini doldurarak XML düzenlemesini daha da kolaylaştırır. Örneğin, aşağıdaki başlangıç etiketini yazarsanız:

 `<book>`

 XML Düzenleyicisi bitiş etiketini doldurur ve imleci başlangıç etiketinden sonra konumlandırır. Aşağıda buna bir örnek verilmiştir ("&#124;" imleç konumunu not edin):

 `<book>`&#124;`</book>`

 Öznitelik değerleri her zaman tırnak içine sahip olması gerektiğinden, XML Düzenleyicisi teklifleri sizin için doldurur. Örneğin, şunu yazarsanız:

 `<book title=`

 XML Düzenleyicisi, tırnakları ekler ve imleci tırnak arasına yerleştirir:

 `<book title="`&#124;`"`

 Benzer şekilde, XML Düzenleyicisi sizin için otomatik olarak aşağıdaki XML sözdizimini de ekler:

- Bir işleme yönergesini sonlandır:  `?>`

- CDATA bloğunu sonlandır: `]]>`

- Açıklamayı bitir: `-->`

- Bir DTD bildirimini sonlandır: `>`

  Bir IntelliSense listesinden nitelenmiş bir ad alanı veya öznitelik seçerseniz ve bu öğenin veya özniteliğin ad alanı henüz kapsamda değilse, XML Düzenleyicisi de bir ad alanı bildirimi ekleyebilme özelliğine sahiptir.

  Örneğin, `e:Book` önekin belgede bildirilmemiş ad alanına bağlandığı IntelliSense listesinden öğesini seçerseniz `http://books` , XML Düzenleyicisi sizin için gerekli olan ad alanı bildirimini ekler. Elde edilen XML metni aşağıda verilmiştir:

  `<e:Book xmlns:e="http://books"`

## <a name="brace-matching"></a>Ayraç eşleştirme
 XML Düzenleyicisi, az önce kapattığınız öğeler hakkında anında geri bildirim sağlamak için küme ayracı vurgulamasını sağlar. Ayrıca, bir küme ayracından eşleşen küme ayracına geçmek için klavye kısayolunu (CTRL +]) de kullanabilirsiniz.

 XML Düzenleyicisi bunu aşağıdaki öğeler için yapar:

- Eşleşen başlangıç ve bitiş etiketleri.

- Herhangi bir " \<" or "> " açılı ayraç çifti.

- Yorumların başlangıcı ve sonu.

- İşlem yönergelerinin başlangıcı ve sonu.

- CDATA blokları başlangıcı ve sonu.

- DTD bildirimlerinin başlangıcı ve sonu.

- Özniteliklerde tırnak açma ve kapatma.

## <a name="modifying-the-intellisense-options"></a>IntelliSense seçeneklerini değiştirme
 IntelliSense ve otomatik tamamlama özellikleri varsayılan olarak etkindir. Ancak, Araçlar-Seçenekler ayarlarınızı değiştirerek bunu değiştirebilirsiniz.

 **Çeşitli** sayfasının **Otomatik Ekle** bölümü aşağıdaki davranışı denetler:

|Ad|Açıklama|
|----------|-----------------|
|Etiketleri kapat|Yeni öğeler için kapatma etiketleri ekler.|
|Öznitelik teklifleri|Yeni bir öznitelik adı girdiğinizde öznitelik değeri tırnakları ekler.|
|Diğer biçimlendirme|Açıklamaları, CDATA, DOCTYPE, işleme yönergelerini ve diğer biçimlendirme bildirimlerini tamamlar.|

#### <a name="to-change-the-auto-completion-behavior"></a>Otomatik tamamlama davranışını değiştirmek için

1. **Araçlar** menüsünde **Seçenekler** ' i seçin.

2. **Metin düzenleyiciyi**genişletin, **XML**' i genişletin ve **çeşitli**' ı seçin.

3. **Otomatik ekleme** bölümünde herhangi bir değişiklik yapıp **Tamam**' a tıklayın.

## <a name="see-also"></a>Ayrıca Bkz.
 [IntelliSense](../ide/using-intellisense.md) [Izlenecek yol: XSLT IntelliSense kullanarak](../xml-tools/walkthrough-using-xslt-intellisense.md) [XML Düzenleyicisi](../xml-tools/xml-editor.md)
