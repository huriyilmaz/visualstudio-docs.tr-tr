---
title: UML bileşen diyagramlarındaki öğelerin özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.componentdiagram.shapes.properties
helpviewer_keywords:
- component diagrams, properties
- UML, element properties
ms.assetid: fa0a9460-6675-4642-aa00-50f8719a892d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 39350a9e1d340651f8e15de109ecf61eb98996bb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671457"
---
# <a name="properties-of-elements-on-uml-component-diagrams"></a>Bileşen diyagramlarındaki öğelerin özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir UML bileşen diyagramında, diyagramdaki her bir öğenin özellikleri vardır. Bir öğenin özelliklerini görmek için diyagramda veya **UML Model Gezgini** ' nde öğeye sağ tıklayın ve ardından **Özellikler**' e tıklayın. Özellikler **, Özellikler penceresinde görünür** .

> [!NOTE]
> Bu konu, UML bileşen diyagramlarındaki öğelerin özellikleri hakkındadır. UML bileşen diyagramlarını okuma hakkında daha fazla bilgi için bkz. [UML Bileşen diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md). UML bileşen diyagramlarını çizme hakkında daha fazla bilgi için bkz. [UML Bileşen diyagramları: yönergeler](../modeling/uml-component-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Öğelerin özellikleri

|Özellik|Varsayılan|Öğe|Açıklama|
|--------------|-------------|-------------|-----------------|
|**Ad**|Varsayılan ad|Tümü|Öğesi tanımlar.|
|**Tam ad**|Ad alanı:: Name|Tümü|Öğeyi benzersiz bir şekilde tanımlar.<br /><br /> Bir bileşene veya türün adına, kendisini içeren paketin tam adı eklenir.<br /><br /> Bir parça veya bağlantı noktasının adına, ona sahip olan bileşenin tam adı eklenir.|
|**İş öğeleri**|0 ilişkili|Tümü|Bu öğeyle ilişkili iş öğelerinin sayısı. İş öğelerini ilişkilendirmek için bkz. [bağlantı modeli öğeleri ve iş öğeleri](../modeling/link-model-elements-and-work-items.md).|
|**Açıklama**|seçim|Tümü|Öğe hakkında genel notları buradan yapabilirsiniz.|
|**Renk**|(tür için varsayılan)|Bileşen, bölüm, yetkilendirme, Bölüm derleme|Şeklin rengi. Diğer özelliklerden farklı olarak bu, şeklin gösterdiği model öğesi yerine şeklin rengidir.|
|**Dolaylı olarak örneklenmiştir**|Doğru|Bileşen|Bileşen yalnızca tasarım yapıtı olarak mevcuttur. Çalışma zamanında yalnızca kendi parçaları vardır.|
|**Soyut**|False|Bileşen|Bileşen tanımı yalnızca, diğer bileşenlerin özelleştiribileceği bir genelleştirme olarak kullanılabilir.|
|**Görünürlük**|Ortak|Bileşen, bölüm, bağlantı noktası|**Genel** -genel olarak görünür.<br /><br /> **Paket** -paket içinde görünür.<br /><br /> **Private** -sahip olan bileşen içinde görünür.<br /><br /> **Korumalı** -sahibinden türetilmiş bileşenlere görünür.|
|**Türüyle**|Oluşturma türü|Bölümüyle<br /><br /> Bağlantı Noktası|Bir bölümün türü bir bileşen veya sınıftır.<br /><br /> Bir bağlantı noktasının türü bir arabirimdir.|
|**Ğunun**|1\.|Bölümüyle<br /><br /> Bağlantı Noktası|Belirtilen türde kaç örnek ana bileşenin parçasını oluşturdığını gösterir.<br /><br /> `1`-tam olarak bir.<br /><br /> `0..1`-bir veya hiçbiri.<br /><br /> `*`-herhangi bir sayı koleksiyonu.<br /><br /> `n..m`-n-k örneklerinden bir koleksiyonu.|
|**Davranış**|False|Bağlantı Noktası|Değer true ise, bu bağlantı noktasına ait iletiler, bileşenin parçaları yerine, bileşeni kapsamında açıklanan etkinlikler veya işlemler tarafından işlenir.|
|**Hizmet**|False|Bağlantı Noktası|True ise, bu bağlantı noktası bu bileşenin yayımlanan arabiriminin bir parçasıdır.|
|**LinkedPackage**|Model|Diyagram|Bu diyagrama eklenen öğeler için varsayılan ad alanı.|

## <a name="see-also"></a>Ayrıca Bkz.
 [UML Kullanım örneği diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md) [UML Kullanım örneği diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)
