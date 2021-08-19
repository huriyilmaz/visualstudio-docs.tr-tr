---
title: XML şema Tasarımcısı XML Düzenleyicisi ile tümleştirme
description: XML şema Tasarımcısı ve XML Düzenleyicisi arasındaki tümleştirmeyi ve bir üzerinde yapılan değişikliklerin diğerine nasıl yansıtıldığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 03b26b7fb9ee44cefe21c92b34c0a35830d63d0b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122098729"
---
# <a name="integration-with-xml-editor"></a>XML düzenleyicisi ile tümleştirme

XML şema Tasarımcısı XML Düzenleyicisi ile tümleşiktir. XML düzenleyicisinde bir XSD dosyasını değiştirirseniz, değişiklik [XML şema Gezgini](../xml-tools/xml-schema-explorer.md)' nde yansıtılır. [Graph görünümü](../xml-tools/graph-view.md) veya [içerik modeli görünümü](../xml-tools/content-model-view.md) açıksa, değişiklik de yansıtılır. XML şema Tasarımcısı ve XML Düzenleyicisi arasında aşağıdaki yollarla gezinebilirsiniz:

- XML düzenleyicisinde, bir düğüme sağ tıklayın ve **XML şema Gezgini 'Nde göster**' i seçin.

- Graph görünümünde ve **XML şema gezgini**' nde bir düğüme çift tıklayın veya bir düğüme sağ tıklayıp **kodu görüntüle**' yi seçin. Içerik modeli görünümünde, bir düğüme sağ tıklayın ve **kodu görüntüle**' yi seçin.

Aşağıdaki ekran görüntüsünde **XML şema Gezgininde** AÇıLAN bir XML şeması gösterilmektedir. **XML şeması Gezgini** , şema kümesini bir ağaç görünümünde görüntüler. XML Düzenleyicisi, şu anda **XML şema Gezgini**'nde etkin olan düğümün metin görünümünü görüntüler.

![xml düzenleyicisi bölmesinde bir xml düğümünü ve xml şeması gezgin bölmesinde şema kümesinin ağaç görünümünü gösteren bir Visual Studio projesinin ekran görüntüsü.](../xml-tools/media/xsddesignerwithxmleditor.gif)

Bazen kodu XML düzenleyicisinde ve grafik tasarımcısında yan yana görmek faydalı olur. Her iki dosyayı aynı anda görüntülemek için, XML düzenleyicisinde herhangi bir yere sağ tıklayın ve **Görünüm Tasarımcısı**' nı seçin. Visual Studio Windows menüsünde **yeni yatay (veya dikey) sekme grubu**' nu seçin.

![görünüm tasarımcısı bölmesini, xml düzenleyicisi bölmesini ve xml şeması gezgin bölmesini gösteren bir Visual Studio projesinin ekran görüntüsü.](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Gezgini](../xml-tools/xml-schema-explorer.md)
