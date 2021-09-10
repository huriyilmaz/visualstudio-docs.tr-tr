---
title: 'İş Akışı Tasarımcısı: Klavye kısayolları'
description: Klavyede yazarak klavyede gezinmek için klavyede İş Akışı Tasarımcısı komutları Visual Studio.
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
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963767"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>İş Akışı Tasarımcısında Klavye Kısayolları

Uygulamanın tüm temel işlevlerine İş Akışı Tasarımcısı klavyeyle erişilebilir.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Klavyeyi kullanarak İş Akışı Tasarımcısı gezinme

Bu Visual Studio, genel kısayollar ve hata ayıklama kısayolları İş Akışı Tasarımcısı. Ayrıca, belirli İş Akışı Tasarımcısı kısayollarını da oluşturabilirsiniz. Bu Visual Studio tüm klavye kısayolları yeniden eşlenmiş olabilir. Ancak, yeniden barındırılan bir uygulamada bu klavye kısayolları sabit koda sahiptir.

### <a name="workflow-designer-keyboard-shortcuts"></a>İş Akışı Tasarımcısı klavye kısayolları

Aşağıdaki tabloda, komutlara atanan varsayılan klavye kısayolları İş Akışı Tasarımcısı özetlenmiştir.

|Kısayol|Amaç|
|-|-------------|
|CTRL+E, A|Bağımsız Değişken Tasarımcısını gösterir veya gizler.|
|CTRL+E, C|Seçili etkinliği yerinde daraltıyor.|
|CTRL+E, E|Seçili etkinliği yerinde genişleter.|
|CTRL+E, F|Seçilen etkinlikleri bir akış çizelgesine bağlar.|
|CTRL+E, I|İçeri Aktarmalar Tasarımcısını gösterir veya gizler.|
|CTRL+E, M|Klavye odağında sekme sırasına göre bir sonraki öğeye taşır.|
|CTRL+E, N|Seçilen etkinliğin (veya en yakın etkinliğin) kapsamında yeni bir değişken oluşturur.|
|CTRL+E, O|Genel Bakış haritasını gösterir veya gizler.|
|CTRL+E, P|Seçili etkinliğin üst öğesine gidin. Bu, iş harita gezintisinde bir düzey yukarı gider ve tasarımcı yüzeyindeki kök etkinliği değiştirir.|
|CTRL+E, S|Klavye odağı olan öğeyi geçerli seçime ekler.|
|CTRL+E, V|Değişken Tasarımcısını gösterir veya gizler.|
|CTRL+E, X|İş akışında tüm etkinlikleri genişleter.|
|CTRL+ALT+F6|Klavye odağını geçerli kullanıcı arabirimi alanından sıranın sonraki alanına taşır. Sıra şu şekildedir:<br /><br /> 1. Breadcrumb gezinti çubuğu.<br />2. Tasarımcı yüzeyi<br />3. Bağımsız değişkenler/Değişkenler/Açıksa içeri aktarmalar tasarımcısı<br />4. Kabuk|

### <a name="flowchart"></a>Akış Çizelgesi

Aşağıdaki listede klavyeyle akış çizelgesi oluşturmak için kullanılan hareketlerle ilgili bilgiler ve bilgiler yer almaktadır. Diğer hizmetlerde olduğu İş Akışı Tasarımcısı, etkinlikler tasarımcı yüzeyine, verilerle birlikte sağlanan genel araç kutusu kısayolları kullanılarak Visual Studio.

- Bir etkinliği taşımak için etkinliği seçin ve ok tuşlarını kullanarak etkinliği yeniden konumlandırin.

- Bir akış çizelgesini yeniden boyutlandırmak için, ok tuşlarını kullanarak bir etkinliği akış çizelgesinin geçerli kenarlığı ötesine getirin. Akış çizelgesi otomatik olarak yeniden boyutlandırılır.

- Bir etkinliği başlangıç düğümü olarak ayarlamak için sağ tıklama **menüsündeKi StartNode** olarak Ayarla komutunu kullanın.

- Etkinliklere bağlanmak için:

    1. Etkinliği sekmeyle seçerek kaynak etkinliği seçin.

    2. Klavye odağını hedef etkinliğine taşımak için gereken sayıda CTRL+E, M tuşlarına basın.

    3. Seçime hedef etkinliği eklemek için CTRL+E, S tuşlarına basın.

    4. Kaynaktan hedefe bağlayıcı eklemek için CTRL+E, F tuşlarına basın.

Etkinlikleri klavyeyle bağlama hakkında notlar:

- CTRL+E, F tuşlarına basmadan önce seçime daha fazla etkinlik ekleyerek aynı anda birden çok bağlantı oluşturabilirsiniz. Bağlantılar, etkinliklerin seçime eklenme sırasına göre yapılır.

- Bir etkinlik çifti bağlanamazsa, örneğin kaynak etkinliğin zaten giden bir bağlantısı varsa, seçime ait etkinlikler arasındaki diğer bağlantılar mümkün olduğunca yine de yapılır.

- Seçime **bir FlowDecision** ekli olduğunda ve **FlowDecision'un** giden bağlayıcısı olmaması, bağlayıcının **True dalı üzerine yerleştirilir.**

### <a name="expression-editing"></a>İfade Düzenleme

Varsayılan olarak, metin düzenlemeye Visual Basic klavye kısayolları aşağıdaki sınırlamalarla birlikte İş Akışı Tasarımcısı düzenleyicisinde uygulanır:

- Aşağıdaki komutların klavye kısayollarını yeniden oluşturmanın hiçbir etkisi yoktur. Bir ifadeyi düzenlerken bu komutlara erişmek için yalnızca varsayılan klavye kısayollarını kullanabilirsiniz.

  - Kes
  - Kopyala
  - Yapıştır
  - Tümünü Seç
  - Geri Al
  - Yinele

- İfade düzenleme komutlarının klavye kısayollarını İş Akışı Tasarımcısı yeniden eşlemek Visual Studio, İş Akışı Tasarımcısı düzenleyin. Metin Düzenleyici kapsamında yapılan değişiklikler otomatik olarak İş Akışı Tasarımcısı. Kısayolları her iki yerde de yeniden eşlemek için değişiklikleri iki kez (her kapsam için bir kez) uygulamalısınız.
