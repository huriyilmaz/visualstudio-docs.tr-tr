---
title: .NET Türüne Gözat ve Seç iletişim kutusu
description: Bir .NET TürüNe Gözat ve Seç iletişim kutusunu kullanarak bir derleme ve proje için derlemelerin ve projelerin ağaç görünümünden bir tür seçmeyi İş Akışı Tasarımcısı.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- dotnet
ms.openlocfilehash: b0258a69738f340ca8a2a58d1c3b900171625e5d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122068137"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>.NET Türüne Gözat ve Seç İletişim Kutusu

Özellikler **penceresinde,** iletişim kutuları veya değişken tasarımcısı gibi tasarımcılar,  veri türleri listesinden Türlere Gözat'ı seçerek Gözat ve **Bir .NET** Türü Seç iletişim kutusudur (kısaltılmış bir formda "tür tarayıcısı" olarak adlandırılır). Bu iletişim kutusunda, derlemelerin ve projelerin ağaç görünümünden bir tür seçebilirsiniz.

Bu iletişim kutusu, aşağıdakiler de dahil olmak üzere çeşitli kullanıcı senaryolarında kullanılır:

- Bir değişkenin veya bağımsız değişkenin türünü ayarlarken.

- Genel etkinlik için bir tür seçme.

- Etkinlikte bir catch <xref:System.Activities.Statements.TryCatch> eklerken.

> [!NOTE]
> Tür tarayıcısı, çok Visual Basic dizi türlerini görüntülemez, ancak çok boyutlu dizi türlerini görüntülemez. Ayrıntılar [için bkz.](/previous-versions/visualstudio/visual-studio-2008/hkhhsz9t(v=vs.90)) Jagged Arrays ve [Multidimensional Arrays.](/previous-versions/visualstudio/visual-studio-2008/d2de1t93(v=vs.90))

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Tür Tarayıcısında Bir Değer veya Başvuru Türü Seçme

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Tür tarayıcısında bir değer veya başvuru türü seçmek için

1. Tür **Adı** kutusuna kullanmak istediğiniz türün adını girin.

2. Aşağıdakilerden birini yapın:

    - Kullanmak istediğiniz türün adı, Tür Adı kutusunda ağaçta  göründüğünde, seçmek için türe çift tıklayın.

    - Kullanmak istediğiniz türü benzersiz **olarak tanımlamak** için Tür Adı kutusuna yeterli karakter yazın ve ardından türü seçmek için Enter tuşuna basın

### <a name="to-select-a-generic-type-from-the-type-browser"></a>Tür tarayıcısında genel bir tür seçmek için

1. Tür **Adı** kutusuna, kullanmak istediğiniz türün adını yazın.

2. Kullanmak istediğiniz türün adı, Tür Adı kutusunda ağaçta  göründüğünde, açılan kutuların görünmesine neden olmak için türü seçin.

     Açılır kutulardan geneli kapatmak için kullanmak istediğiniz türü seçin ve ardından Tamam'a **tıklayın.**

## <a name="types-displayed-in-the-type-browser"></a>Tür tarayıcısında görüntülenen türler

Tür tarayıcısında görüntülenen türler, tür tarayıcısının nasıl başlatıldıklarına bağlı olarak değişebilir. Tür tarayıcısı **vs2010** içindeki bir iş akışı projesinden başlatıldı ise, varsayılan olarak başvurulan derlemelerde ve başvurulan projelerde tüm türler gösterilir. Tür tarayıcısı **vs2010** proje sisteminin dışından (yeniden barındırılan bir iş akışı uygulamasında veya tek başına bir iş akışı dosyasında olduğu gibi) başlatıldı ise, varsayılan olarak AppDomain'de yüklenen tüm derlemelerin türleri gösterilir.

Tür tarayıcısında türler etkinlik tasarımcısı geliştiricileri tarafından filtrelenmiş olabilir. Belirli bir etkinlik için türlerin yalnızca bir alt kümesini görebilir. Örneğin, <xref:System.Activities.Statements.TryCatch> etkinlikte tür tarayıcısında yalnızca <xref:System.Exception> tür türlerinden türetilen türler gösterilir.

## <a name="filtering-search-results-in-the-type-browser"></a>Tür Tarayıcısında Arama Sonuçlarını Filtreleme

Bir eşleşmeyi bulmak için **daha fazla karakter** yazdıkça Tür Adı kutusunda türlerin listesi kısalır. Yalnızca tam adı, sizin yazmış olduğunuz dizeyle başlayan veya kısa adı, yazmış olduğunuz dizeyle başlayan türler filtrelenmiş listede görüntülenir.

Örnek:

1. Yazma **işlemi** eşleni, <xref:System.OperationCanceledException> ancak ile <xref:System.InvalidOperationException> eşleşmez. eşleşmesi <xref:System.InvalidOperationException> için System.I veya Invalid yazmaya başlayın.

2. Genel **eşleşmeler** <xref:System.GenericUriParser> yazarak ad alanına tür <xref:System.Collections.Generic> yazmazsınız. Ad alanı içinde türleri <xref:System.Collections.Generic> aramak için ad alanının tam adını yazın.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Tür tarayıcısı iletişim kutusunu kullanarak hizmet sözleşmesini seçme

Hizmet sözleşmesi türü seçen tür tarayıcısı yalnızca özniteliğine sahip türleri <xref:System.ServiceModel.ServiceContractAttribute> gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- [Etkinlik Tasarımcılarını kullanma](control-flow-activity-designers.md)
