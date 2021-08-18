---
title: 'İş Akışı Tasarımcısı: klavye kısayolları'
description: Visual Studio içinde İş Akışı Tasarımcısı gezinmek için klavyede kullanabileceğiniz çeşitli komutları öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 4dcf52de12d2c6401a7715f36ad80ecfd6ed9f4f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045846"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>İş Akışı Tasarımcısında Klavye Kısayolları

İş Akışı Tasarımcısı tüm temel işlevlerine klavye tarafından erişilebilir.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Klavyeyi kullanarak İş Akışı Tasarımcısı gezinme

Visual Studio içinde, genel kısayollar ve hata ayıklama kısayolları İş Akışı Tasarımcısı için geçerlidir. Ayrıca, bazı İş Akışı Tasarımcısı belirli klavye kısayolları oluşturulmuştur. Visual Studio, tüm klavye kısayolları yeniden eşlenir. Ancak, yeniden barındırılan bir uygulamada, bu klavye kısayolları sabit olarak kodlanmıştır.

### <a name="workflow-designer-keyboard-shortcuts"></a>Klavye kısayollarını İş Akışı Tasarımcısı

Aşağıdaki tabloda İş Akışı Tasarımcısı komutlarına atanan varsayılan klavye kısayolları özetlenmektedir.

|Kısayol|Amaç|
|-|-------------|
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

Aşağıdaki listede klavye tarafından akış çizelgesi oluşturmak için kullanılan hareketler gösterilmektedir. İş Akışı Tasarımcısı kalanında olduğu gibi, Etkinlikler, Visual Studio birlikte sunulan genel araç kutusu kısayollarını kullanarak tasarımcı yüzeyine eklenir.

- Bir etkinliği taşımak için etkinliği seçin ve ok tuşlarını kullanarak yeniden konumlandırın.

- Bir akış çizelgesini yeniden boyutlandırmak için, ok tuşlarını kullanarak bir etkinliği akış çizelgesinin geçerli kenarlığının ötesine taşıyın. Akış çizelgesi otomatik olarak yeniden boyutlandırılır.

- Bir etkinliği başlangıç düğümü olarak ayarlamak için sağ tıklama menüsünde **StartNode olarak ayarla** komutunu kullanın.

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

varsayılan olarak, Visual Basic metin düzenleme için varsayılan klavye kısayolları aşağıdaki sınırlamalarla birlikte İş Akışı Tasarımcısı ifade düzenleyicisi içinde geçerlidir:

- Aşağıdaki komutlar için klavye kısayollarının yeniden eşleştirbir etkisi yoktur. Bir ifadeyi düzenlediğinizde bu komutlara erişmek için yalnızca varsayılan klavye kısayollarını kullanabilirsiniz.

  - Kes
  - Kopyala
  - Yapıştır
  - Tümünü Seç
  - Geri Al
  - Yinele

- Visual Studio İş Akışı Tasarımcısı içindeki ifade düzenleme komutlarının klavye kısayollarını yeniden eşlemek için İş Akışı Tasarımcısı kapsamındaki kısayolları düzenleyin. Metin düzenleyici kapsamında yapılan değişiklikler İş Akışı Tasarımcısı için otomatik olarak uygulanmaz. Her iki yerde de kısayolları yeniden eşlemek isterseniz, değişiklikleri iki kez uygulamanız gerekir (her kapsam için bir kez).
