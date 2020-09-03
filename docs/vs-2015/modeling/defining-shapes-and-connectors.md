---
title: Şekilleri ve bağlayıcıları tanımlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 1fae548d-9288-4dd5-a24f-ff0d69c73628
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8304e573f64671936eee2ce922b904b41187aad2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669851"
---
# <a name="defining-shapes-and-connectors"></a>Şekiller ve Bağlayıcıları Tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir diyagramda, etki alanına özgü dil (DSL) içindeki bilgileri göstermek için kullanabileceğiniz birkaç temel şekil türü vardır.

## <a name="basic-types-of-shapes-and-connectors"></a><a name="shapeTypes"></a> Temel şekil ve bağlayıcı türleri
 DSL diyagramı çizgiler veya *Bağlayıcılar*ile birbirine bağlanmış *şekillerin* bir koleksiyonunu gösterir.  Genellikle, ancak her zaman değildir:

- Şekiller model öğelerinin görünür gösterimidir.

- Bağlayıcılar başvuru ilişkilerini temsil eder.

- Diyagram, model kök örneğini temsil eder.

- Model öğeleri arasında ilişkiler katıştırma kapsama göre gösterilir. Örneğin, bileşen bağlantı noktalarını temsil eden öğeler bileşene katıştırılır.

  Bu desenler zorlanmaz, ancak daha güçlü bir şekilde desteklenir. Bir DSL tasarladığınızda, ekleme ilişkilerinin tasarımının, modeli ekranda nasıl sunmak istediğinizin etkilenmeyeceğini göz önünde bulundurun. Buna karşılık, başvuru ilişkileri iş etki alanınız kavramlarını yansıtmalıdır.

  Aşağıdaki şekil türleri kullanılabilir:

|Şekil türü|Description|
|----------------|-----------------|
|Geometri şekli|Genel amaçlı dikdörtgen veya elips şekil. Şeklin sınırlarına göre belirli konumlarda metin ve simge dekoratlarını gösterebilirsiniz.<br /><br /> Şekilleri geometri şekillerinin içine yerleştirmek için bkz. [şekilleri Iç Içe geçme](../modeling/nesting-shapes.md).|
|Bölme şekli|Bir UML sınıfı gibi üst bilgi ve bölmeleri içeren dikdörtgen. Her bölme, bir metin satırları listesi içerebilir.<br /><br /> Satırlar genellikle şeklin gösterdiği öğe altında gömülü öğeleri temsil eder. Bir örnek için, sınıf diyagramları çözüm şablonundan DSL oluşturun.|
|Resim şekli|Bir görüntüyü görüntüleyen şekil.|
|Bağlantı noktası şekli|Başka bir şeklin ana hattını eklemek için tasarlanan küçük bir dikdörtgen. Genellikle bileşen modellerinde kullanılır.<br /><br /> Bir bağlantı noktasıyla temsil edilen model öğesi, genellikle üst şekille temsil edilen öğe altına katıştırılır. Bir örnek için, bileşenler çözüm şablonunu kullanarak bir DSL oluşturun.<br /><br /> Varsayılan olarak, bir bağlantı noktası şekli, üst öğesinin yüzlerinin yanında yer alabilir. Belirli bir konumla sınırlamak için bir sınır kuralı tanımlayabilirsiniz.<br /><br /> Bağlantı noktası şeklini çok küçük ve saydam hale getirerek, üst şeklinin yüzeyinde sabit bir bağlantı noktası sağlamak için bunu kullanabilirsiniz.|
|Lardır|Bir diyagramı yatay veya dikey kesimlerde bölüm olarak birleştirir. Kulvar her zaman diyagramdaki diğer şekillerin altında kalır.<br /><br /> Genellikle kulvarın model öğeleri, model kökünün üst öğesi ve diğer öğeleri ise üst öğesi. Bir örnek için, görev akışı çözüm şablonundan bir DSL oluşturun.|
|Bağlayıcılar|Şekiller arasında çizilen satırlar genellikle başvuru ilişkilerini temsil eder. Bağlayıcıyı düz veya dikdörtgen hale getirmek ve farklı türde ok türlerine sahip olmak için seçenekleri ayarlayabilirsiniz.|

## <a name="shape-inheritance"></a><a name="shapeInheritance"></a> Şekil Devralma
 Bir şekil, başka bir şekilden devralınabilir. Ancak, şekillerin aynı türde olması gerekir. Örneğin, yalnızca bir geometri şekli geometri şeklinin içinden devralınabilir. Devralınan şekiller, temel şeklinin bölmeleri ve dekoratlarını barındırır. Bağlayıcılar bağlayıcılardan kalıtımla alabilir.
