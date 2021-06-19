---
title: Şekiller ve Bağlayıcıları Tanımlama
description: Bir diyagram üzerinde, etki alanına özgü bir dilde (DSL) bilgi göstermek için kullanabileceğiniz çeşitli temel şekil türleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 622ff598ac2471814e51b0e268c12d40e726fb98
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385753"
---
# <a name="define-shapes-and-connectors"></a>Şekilleri ve bağlayıcıları tanımlama

Bir diyagramda, etki alanına özgü dil (DSL) içindeki bilgileri göstermek için kullanabileceğiniz birkaç temel şekil türü vardır.

## <a name="basic-types-of-shapes-and-connectors"></a><a name="shapeTypes"></a> Temel şekil ve bağlayıcı türleri

DSL diyagramı çizgiler veya *Bağlayıcılar* ile birbirine bağlanmış *şekillerin* bir koleksiyonunu gösterir. Genellikle, ancak her zaman değildir:

- Şekiller model öğelerinin görünür gösterimidir.

- Bağlayıcılar başvuru ilişkilerini temsil eder.

- Diyagram, model kök örneğini temsil eder.

- Model öğeleri arasında ilişkiler katıştırma kapsama göre gösterilir. Örneğin, bileşen bağlantı noktalarını temsil eden öğeler bileşene katıştırılır.

Bu desenler zorlanmaz, ancak daha güçlü bir şekilde desteklenir. Bir DSL tasarladığınızda, ekleme ilişkilerinin tasarımının, modeli ekranda nasıl sunmak istediğinizin etkilenmeyeceğini göz önünde bulundurun. Buna karşılık, başvuru ilişkileri iş etki alanınız kavramlarını yansıtmalıdır.

Aşağıdaki şekil türleri kullanılabilir:

|Şekil türü|Açıklama|
|-|-|
|Geometri şekli|Genel amaçlı dikdörtgen veya elips şekil. Şeklin sınırlarına göre belirli konumlarda metin ve simge dekoratlarını gösterebilirsiniz. Ayrıca, şekilleri geometri şekillerinin içinde iç içe geçirebilirsiniz.|
|Bölme şekli|Bir UML sınıfı gibi üst bilgi ve bölmeleri içeren dikdörtgen. Her bölme, bir metin satırları listesi içerebilir.<br /><br /> Satırlar genellikle şeklin gösterdiği öğe altında gömülü öğeleri temsil eder. Bir örnek için, sınıf diyagramları çözüm şablonundan DSL oluşturun.|
|Resim şekli|Bir görüntüyü görüntüleyen şekil.|
|Bağlantı noktası şekli|Başka bir şeklin ana hattını eklemek için tasarlanan küçük bir dikdörtgen. Genellikle bileşen modellerinde kullanılır.<br /><br /> Bir bağlantı noktasıyla temsil edilen model öğesi, genellikle üst şekille temsil edilen öğe altına katıştırılır. Bir örnek için, bileşenler çözüm şablonunu kullanarak bir DSL oluşturun.<br /><br /> Varsayılan olarak, bir bağlantı noktası şekli, üst öğesinin yüzlerinin yanında yer alabilir. Belirli bir konumla sınırlamak için bir sınır kuralı tanımlayabilirsiniz.<br /><br /> Bağlantı noktası şeklini çok küçük ve saydam hale getirerek, üst şeklinin yüzeyinde sabit bir bağlantı noktası sağlamak için bunu kullanabilirsiniz.|
|Lardır|Bir diyagramı yatay veya dikey kesimlerde bölüm olarak birleştirir. Kulvar her zaman diyagramdaki diğer şekillerin altında kalır.<br /><br /> Genellikle kulvarın model öğeleri, model kökünün üst öğesi ve diğer öğeleri ise üst öğesi. Bir örnek için, görev akışı çözüm şablonundan bir DSL oluşturun.|
|Bağlayıcılar|Şekiller arasında çizilen satırlar genellikle başvuru ilişkilerini temsil eder. Bağlayıcıyı düz veya dikdörtgen hale getirmek ve farklı türde ok türlerine sahip olmak için seçenekleri ayarlayabilirsiniz.|

## <a name="shape-inheritance"></a>Şekil Devralma

Bir şekil, başka bir şekilden devralınabilir. Ancak, şekillerin aynı türde olması gerekir. Örneğin, yalnızca bir geometri şekli geometri şeklinin içinden devralınabilir. Devralınan şekiller, temel şeklinin bölmeleri ve dekoratlarını barındırır. Bağlayıcılar bağlayıcılardan kalıtımla alabilir.
