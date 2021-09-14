---
title: 'Nasıl: Özel Galeri Hesabı için Atom Akışı | Microsoft Docs'
description: Uzantılar içeren bir intranet konuma Atom (RSS) akışı oluşturabilir ve akışı Özel galeri olarak Uzantılar ve Güncelleştirmeler'e ebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8ff57a36930ebf1ad248480cd7ea15a50440529b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626264"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Nasıl yapılır: Özel galeri için Atom akışı oluşturma
Uzantılar içeren bir intranet konuma Atom (RSS) akışı oluşturabilir ve  akışı Özel galeri olarak Uzantılar ve Güncelleştirmeler'e ebilirsiniz. Daha fazla bilgi için bkz. [Özel galeriler.](../extensibility/private-galleries.md)

## <a name="create-an-atom-feed"></a>Atom akışı oluşturma
 Özel galeri olarak atom akışı oluşturmak için önce uzantılarınızı *(.vsix* dosyaları) bir klasöre toplayın. 8. alt klasörlere göre düzenleyebilirsiniz. Ayrıca aşağıdaki kaynaklara da ihtiyacınız vardır:

- Uzantıları *atom.xml* galeri olarak kullanılabilir yapan bir dosya. Uzantılar ve Güncelleştirmeler'e *atom.xml* hakkında bilgi için **bkz.** [Özel galeriler.](../extensibility/private-galleries.md)

- Uzantılardan ayıklanan tüm görüntü dosyalarını içeren bir klasör (örneğin, ekran görüntüleri). Dosya *atom.xml,* Uzantılar ve Güncelleştirmeler'de kullanılabilir olacak şekilde bu **görüntülerin göreli bağlantılarını içerir.**

  Örneğin, aşağıdaki iki uzantıyı bir klasöre toplanmış olduğunu varsayalım:

- Template_Wizard_239 VSIX proje şablonu olan *Template_Wizard_239.vsix.*

- Seçili bir sözcüğün tüm örneklerini vurgulamaya yönelik bir araç olan *SelectionHighlight.vsix.*

  atom.xml *dosyasının* içeriği aşağıdaki örnekteki gibi olabilir:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title type="text" />
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>
  <updated>2011-04-14T21:25:48Z</updated>
  <entry>
    <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>
    <title type="text">Highlight all occurrences of selected word</title>
    <summary type="text">This extends the editor to highlight ....</summary>
    <published>2011-04-14T14:24:51-07:00</published>
    <updated>2011-04-14T14:24:22-07:00</updated>
    <author>
      <name>Microsoft</name>
    </author>
    <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />
    <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />
    <content type="application/octet-stream" src="SelectionHighlight.vsix" />
    <Vsix xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>
      <Version>1.31</Version>
      <References />
      <Rating xsi:nil="true" />
      <RatingCount xsi:nil="true" />
      <DownloadCount xsi:nil="true" />
    </Vsix>
  </entry>
  <entry>
    <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>
    ...
  </entry>
</feed>
```

 İki bağlantı etiketi, görüntülerin oluşturulan klasöründeki ekran görüntülerine başvurur.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel galeriler](../extensibility/private-galleries.md)
