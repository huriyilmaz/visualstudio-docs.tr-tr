---
title: XML Düzenleyicisi ile XML Şema Tasarımcısı tümleştirmesi
description: XML Şema Tasarımcısı ile XML düzenleyicisi arasındaki tümleştirmeyi ve bir xml düzenleyicisinde yapılan değişikliklerin diğer tasarımcıya nasıl yansıdığını öğrenin.
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
ms.openlocfilehash: 9ca0996faba3f154799dd9b292e892dfa11e3be7e6b7f86c0f8dceb0bd638160
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121423675"
---
# <a name="integration-with-xml-editor"></a>XML düzenleyicisi ile tümleştirme

XML Şema Tasarımcısı, XML düzenleyicisiyle tümleştirilmiştir. XML düzenleyicisinde bir XSD dosyasını değiştirirsiniz, değişiklik XML Şema [Gezgini'ne yansıtıldı.](../xml-tools/xml-schema-explorer.md) Graph Görünümü [veya](../xml-tools/graph-view.md) İçerik Modeli [Görünümü açıksa,](../xml-tools/content-model-view.md) değişiklik de bu görünüme yansıttır. XML Şema Tasarımcısı ile XML düzenleyicisi arasında aşağıdaki yollarla gezinebilirsiniz:

- XML düzenleyicisinde bir düğüme sağ tıklayın ve XML Şema **Gezgini'nde Göster'i seçin.**

- Görünüm Graph **XML** Şema Gezgini'nde bir düğüme çift tıklayın veya bir düğüme sağ tıklar ve Kodu Görüntüle'yi **seçin.** İçerik Modeli Görünümünde bir düğüme sağ tıklayın ve Kodu **Görüntüle'yi seçin.**

Aşağıdaki ekran görüntüsünde, XML Şema Gezgini'nde açılan **bir XML Şeması gösterilmektedir.** **XML Şema Gezgini,** şema kümesi ağaç görünümünde görüntüler. XML düzenleyicisi, XML Şema Gezgini'nde şu anda etkin olan düğümün **metin görünümünü görüntüler.**

![XML Düzenleyicisi Visual Studio XML düğümünü ve XML Şema Gezgini bölmesinde ayarlanmış şemanın ağaç görünümünü gösteren bir xml projesinin ekran görüntüsü.](../xml-tools/media/xsddesignerwithxmleditor.gif)

Bazen kodu XML düzenleyicisinde ve grafik tasarımcısında yan yana görmek yararlı olabilir. Her iki dosyanın da aynı anda görüntülemek için XML düzenleyicisinde herhangi bir yere sağ tıklayın ve **öğesini** Görünüm Tasarımcısı. Dikey Visual Studio Windows Yeni Yatay **(veya Dikey) Sekme Grubu seçeneğini belirleyin.**

![Görünüm Tasarımcısı bölmesini, XML Düzenleyicisi bölmesini ve XML Şema Gezgini bölmesini gösteren bir Visual Studio projesinin ekran görüntüsü.](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Gezgini](../xml-tools/xml-schema-explorer.md)
