---
title: Nasıl? Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72fbf2d3973ffd84de1cf6f33788c43511c3ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711009"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Nasıl yapilir: Özel bir galeri için Atom beslemesi oluşturma
Uzantılar içeren bir intranet konumuna atom (RSS) akışı oluşturabilir ve özet akışını özel galeri olarak **Uzantılar ve Güncelleştirmeler'e** ekleyebilirsiniz. Daha fazla bilgi için [bkz.](../extensibility/private-galleries.md)

## <a name="create-an-atom-feed"></a>Atom beslemesi oluşturma
 Özel galeri olarak atom akışı oluşturmak için önce uzantılarınızı *(.vsix* dosyaları) bir klasörde toplarsınız. İsterseniz alt klasörler halinde düzenleyebilirsiniz. Ayrıca aşağıdaki kaynaklara ihtiyacınız olacaktır:

- Uzantıları özel galeri olarak kullanılabilir kılan bir *atom.xml* dosyası. *atom.xml* dosyasının **Uzantılar ve Güncellemeler'e**nasıl bağlanılabildiğini öğrenmek için [bkz.](../extensibility/private-galleries.md)

- Uzantılardan çıkarılan görüntü dosyalarını içeren bir klasör (örneğin, ekran görüntüleri). *Atom.xml* dosyası, **uzantılar ve güncellemeler**mevcuttur, böylece bu görüntülere göreli bağlantılar içerir.

  Örneğin, aşağıdaki iki uzantıyı bir klasörde topladığınızı varsayalım:

- *Template_Wizard_239.vsix*, boş bir VSIX proje şablonudur.

- Seçili sözcüğün tüm örneklerini vurgulamak için bir araç olan *SelectionHighlight.vsix.*

  *atom.xml* dosyasının içeriği aşağıdaki örneğe benzer:

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

 İki bağlantı etiketinin görüntülerin oluşturulan klasöründeki ekran görüntülerine atıfta bulunduğuna dikkat edin.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel galeriler](../extensibility/private-galleries.md)
