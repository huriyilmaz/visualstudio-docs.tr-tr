---
title: UML Kullanım örneği diyagramlarında öğelerin özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties
- vs.teamarch.usecasediagram.shapes.properties
helpviewer_keywords:
- use case diagrams, properties
ms.assetid: 2728fb26-a275-4fce-8a2c-5a78af6bee04
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db3dc649d979c87960a42d38ffa211e352be175b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671409"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>UML kullanım durumu diyagramlarındaki öğelerin özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML Kullanım örneği diyagramında, diyagramdaki her bir öğenin özellikleri vardır. Bir öğenin özelliklerini görmek için diyagramda veya **UML Model Gezgini** ' nde öğeye sağ tıklayın ve ardından **Özellikler**' e tıklayın. Özellikler **, Özellikler penceresinde görünür** .

> [!NOTE]
> Bu konu, UML Kullanım örneği diyagramlarındaki öğelerin özellikleri hakkındadır. UML etkinlik diyagramlarını okuma hakkında daha fazla bilgi için bkz. [UML Kullanım örneği diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md). UML etkinlik diyagramlarını çizme hakkında daha fazla bilgi için bkz. [UML Kullanım örneği diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Öğelerin özellikleri

|Özellik|Varsayılan|Öğe|Açıklama|
|--------------|-------------|-------------|-----------------|
|**Ad**|Varsayılan ad|Tümü|Öğesi tanımlar.|
|**Tam ad**|Paket:: Name|Tümü|Öğeyi benzersiz bir şekilde tanımlar. Ön eki içeren paketin tam adı.|
|**İş öğeleri**|0 ilişkili|Tümü|Bu öğeyle ilişkili iş öğelerinin sayısı. İş öğelerini ilişkilendirmek için bkz. [bağlantı modeli öğeleri ve iş öğeleri](../modeling/link-model-elements-and-work-items.md).|
|**Açıklama**|(yok)|Tümü|Öğe hakkında genel notları buradan yapabilirsiniz.|
|**Color**|(varsayılan)|Tümü|Şeklin rengi. Diğer özelliklerden farklı olarak, bu, şeklin gösterdiği öğenin bir özelliği değildir.|
|**Görüntü yolu**|(yok)|Actor (Oyuncu)|Varsayılan aktör simgesi yerine kullanılması gereken bir görüntünün dosya yolu. Simgenin Visual Studio projesi içindeki bir kaynak dosyası olması gerekir.|
|**Konular**|(yok)|Kullanım Örneği|Kullanım örneğine sahip olan alt sistem veya diğer tür.<br /><br /> Bu ayarı, kullanım durumunu diyagramdaki bir alt sisteme yerleştirerek ayarlayabilirsiniz.|
|**Görünürlük**|Genel|Kullanım örneği, aktör, alt sistem|**Genel** -genel olarak görünür.<br /><br /> **Paket** -paket içinde görünür.|
|**IsAbstract**|Yanlış|Kullanım örneği, aktör, alt sistem|True ise tür başlatılamaz ve diğer tanımlara göre özelleştirme için temel olarak tasarlanmıştır.|
|**Dolaylı olarak örneklenmiştir**|Doğru|Sistemin|Alt sistem yalnızca tasarım yapıtı olarak mevcuttur. Çalışma zamanında yalnızca kendi parçaları vardır.|
|**Köprü**|(yok)|Yapıt|Yapıtın bir bağlantı sağladığı diyagramın veya belgenin URL veya dosya yolu.|

 İlişkilerin özelliklerinin bir listesi için bkz. [UML sınıf diyagramlarındaki Ilişkilerin özellikleri](../modeling/properties-of-associations-on-uml-class-diagrams.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [UML Kullanım örneği diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md) [UML Kullanım örneği diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)
