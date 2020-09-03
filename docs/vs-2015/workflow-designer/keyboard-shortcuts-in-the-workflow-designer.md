---
title: İş Akışı Tasarımcısı klavye kısayolları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6f7bc701c4a7009d402c778356a290ce4e129bb3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658966"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>İş Akışı Tasarımcısında Klavye Kısayolları
Uygulamasının tüm temel işlevlerine [!INCLUDE[wfd1](../includes/wfd1-md.md)] klavye tarafından erişilebilir.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Klavyeyi kullanarak İş Akışı Tasarımcısı gezinme
 İçinde [!INCLUDE[vs2010](../includes/vs2010-md.md)] , genel kısayollar ve hata ayıklama kısayolları için geçerlidir [!INCLUDE[wfd2](../includes/wfd2-md.md)] . Ayrıca, bazı [!INCLUDE[wfd2](../includes/wfd2-md.md)] belirli klavye kısayolları oluşturulmuştur. [!INCLUDE[vs2010](../includes/vs2010-md.md)]' De, tüm klavye kısayolları yeniden eşlenir. Ancak, yeniden barındırılan bir uygulamada, bu klavye kısayolları sabit olarak kodlanmıştır.

### <a name="workflow-designer-keyboard-shortcuts"></a>Klavye kısayollarını İş Akışı Tasarımcısı
 Aşağıdaki tabloda, komutlara atanan varsayılan klavye kısayolları özetlenmektedir [!INCLUDE[wfd2](../includes/wfd2-md.md)] .

|Kısayol|Amaç|
|--------------|-------------|
|CTRL + E, A|Bağımsız değişken tasarımcısını gösterir veya gizler.|
|CTRL + E, C|Seçili aktiviteyi yerinde daraltır.|
|CTRL + E, E|Seçili aktiviteyi yerinde genişletir.|
|CTRL + E, F|Seçilen etkinlikleri bir akış çizelgesine bağlar.|
|CTRL + E, ı|Içeri aktarmalar tasarımcısını gösterir veya gizler.|
|CTRL + E, M|Klavye odağını sekme düzeninde bir sonraki öğeye kaydırır.|
|CTRL + E, N|Seçilen etkinliğin kapsamında (veya en yakın) yeni bir değişken oluşturur.|
|CTRL + E, O|Genel bakış haritasını gösterir veya gizler.|
|CTRL + E, P|Seçili etkinliğin üst öğesine gider. Bu, içerik haritası gezinmede bir düzey yukarı gider ve tasarımcı yüzeyinde kök etkinliği değiştirir.|
|CTRL + E, S|Klavye odağının bulunduğu öğeyi geçerli seçime ekler.|
|CTRL + E, V|Değişken tasarımcısını gösterir veya gizler.|
|CTRL + E, X|İş akışındaki tüm etkinlikleri genişletir.|
|CTRL + ALT + F6|Klavye odağını geçerli kullanıcı arabirimi alanından dizideki bir sonraki alana kaydırır. Sıra aşağıdaki gibidir:<br /><br /> 1. içerik haritası gezinti çubuğu.<br />2. tasarımcı yüzeyi<br />3. açık ise bağımsız değişkenler/değişkenler/Içeri aktarma Tasarımcısı<br />4. Shell|

### <a name="flowchart"></a>Akış Çizelgesi
 Aşağıdaki listede klavye tarafından akış çizelgesi oluşturmak için kullanılan hareketler gösterilmektedir. ' In geri kalanında olduğu gibi [!INCLUDE[wfd2](../includes/wfd2-md.md)] Etkinlikler, ile birlikte sunulan genel araç kutusu kısayollarını kullanarak tasarımcı yüzeyine eklenir [!INCLUDE[vs2010](../includes/vs2010-md.md)] .

- Bir etkinliği taşımak için etkinliği seçin ve ok tuşlarını kullanarak yeniden konumlandırın.

- Bir akış çizelgesini yeniden boyutlandırmak için, ok tuşlarını kullanarak bir etkinliği akış çizelgesinin geçerli kenarlığının ötesine taşıyın. Akış çizelgesi otomatik olarak yeniden boyutlandırılır.

- Bir etkinliği başlangıç düğümü olarak ayarlamak için bağlam menüsünde **StartNode olarak ayarla** komutunu kullanın.

- Etkinlikleri bağlamak için:

  1. Etkinliğe göre sekmeye tıklayarak Kaynak etkinliğini seçin.

  2. Klavye odağını hedef etkinliğe taşımak için gereken sayıda CTRL + E, M tuşuna basın.

  3. Hedef etkinliği seçime eklemek için CTRL + E, S tuşlarına basın.

  4. Bağlayıcıyı kaynaktan hedefe eklemek için CTRL + E, F tuşlarına basın.

  Etkinlikleri klavyeye göre bağlama hakkında notlar:

- CTRL + E, F tuşlarına basmadan önce seçime daha fazla etkinlik ekleyerek aynı anda birden fazla bağlantı yapabilirsiniz. Bağlantılar, etkinliklerin seçime eklendiği sırada yapılır.

- Bir dizi çiftin bağlantısı yapılaamadığında Örneğin, kaynak etkinliğin zaten bir giden bağlantısı varsa, seçimdeki etkinlikler arasındaki diğer bağlantılar mümkün olduğunda yine de yapılabilir.

- Seçime bir **flowkararı** dahil edildiğinde ve **flowkararının** giden bağlayıcıları yoksa, bağlayıcı **doğru** dala yerleştirilir.

### <a name="expression-editing"></a>İfade düzenlemesi
 Varsayılan olarak, metin düzenleme için varsayılan klavye kısayolları [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , içindeki ifade Düzenleyicisi içinde [!INCLUDE[wfd2](../includes/wfd2-md.md)] aşağıdaki sınırlamalara göre geçerlidir:

- Aşağıdaki komutlar için klavye kısayollarının yeniden eşleştirbir etkisi yoktur. Bir ifadeyi düzenlediğinizde bu komutlara erişmek için yalnızca varsayılan klavye kısayollarını kullanabilirsiniz.

    1. Kes

    2. Kopyala

    3. Yapıştır

    4. Tümünü Seç

    5. Geri Al

    6. Yinele

- İçindeki içindeki ifade düzenleme komutlarının klavye kısayollarını yeniden eşlemek için [!INCLUDE[wfd2](../includes/wfd2-md.md)] [!INCLUDE[vs2010](../includes/vs2010-md.md)] , kapsamdaki kısayolları düzenleyin [!INCLUDE[wfd2](../includes/wfd2-md.md)] . Metin düzenleyici kapsamında yapılan değişiklikler için otomatik olarak uygulanmaz [!INCLUDE[wfd2](../includes/wfd2-md.md)] . Her iki yerde de kısayolları yeniden eşlemek isterseniz, değişiklikleri iki kez uygulamanız gerekir (her kapsam için bir kez).