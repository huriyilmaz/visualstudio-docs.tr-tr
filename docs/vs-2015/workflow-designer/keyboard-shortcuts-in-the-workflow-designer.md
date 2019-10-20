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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658966"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>İş Akışı Tasarımcısında Klavye Kısayolları
@No__t_0 tüm temel işlevlerine klavye tarafından erişilebilir.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Klavyeyi kullanarak İş Akışı Tasarımcısı gezinme
 @No__t_0 içinde, genel kısayollar ve hata ayıklama kısayolları [!INCLUDE[wfd2](../includes/wfd2-md.md)] için geçerlidir. Ayrıca, bazı [!INCLUDE[wfd2](../includes/wfd2-md.md)] belirli klavye kısayolları oluşturulmuştur. @No__t_0, tüm klavye kısayolları yeniden eşlenir. Ancak, yeniden barındırılan bir uygulamada, bu klavye kısayolları sabit olarak kodlanmıştır.

### <a name="workflow-designer-keyboard-shortcuts"></a>Klavye kısayollarını İş Akışı Tasarımcısı
 Aşağıdaki tabloda [!INCLUDE[wfd2](../includes/wfd2-md.md)] komutlarına atanan varsayılan klavye kısayolları özetlenmektedir.

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
 Aşağıdaki listede klavye tarafından akış çizelgesi oluşturmak için kullanılan hareketler gösterilmektedir. @No__t_0 kalanında olduğu gibi, Etkinlikler, [!INCLUDE[vs2010](../includes/vs2010-md.md)] birlikte sunulan genel araç kutusu kısayollarını kullanarak tasarımcı yüzeyine eklenir.

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
 Varsayılan olarak, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] metin düzenleme için varsayılan klavye kısayolları aşağıdaki sınırlamalarla birlikte [!INCLUDE[wfd2](../includes/wfd2-md.md)] ifade Düzenleyicisi içinde geçerlidir:

- Aşağıdaki komutlar için klavye kısayollarının yeniden eşleştirbir etkisi yoktur. Bir ifadeyi düzenlediğinizde bu komutlara erişmek için yalnızca varsayılan klavye kısayollarını kullanabilirsiniz.

    1. Kes

    2. Kopyala

    3. Yapıştır

    4. Tümünü Seç

    5. Komutunu

    6. Yinele

- @No__t_1 [!INCLUDE[wfd2](../includes/wfd2-md.md)] içindeki ifade düzenleme komutlarının klavye kısayollarını yeniden eşlemek için [!INCLUDE[wfd2](../includes/wfd2-md.md)] kapsamındaki kısayolları düzenleyin. Metin düzenleyici kapsamında yapılan değişiklikler [!INCLUDE[wfd2](../includes/wfd2-md.md)] için otomatik olarak uygulanmaz. Her iki yerde de kısayolları yeniden eşlemek isterseniz, değişiklikleri iki kez uygulamanız gerekir (her kapsam için bir kez).