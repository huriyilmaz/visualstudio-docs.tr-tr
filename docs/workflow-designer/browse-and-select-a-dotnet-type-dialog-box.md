---
title: .NET tür iletişim kutusuna gözatıp seçin
description: İş Akışı Tasarımcısı ' deki derlemelerin ve projelerin ağaç görünümünden bir tür seçmek için bir .NET türü görüntüle ve Seç iletişim kutusunu nasıl kullanabileceğinizi öğrenin.
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
ms.openlocfilehash: f14fe6095011e77341803c0cdeda5bcd94f0eb8805644859b5c2d6d4e8709481
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121423767"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>.NET Türüne Gözat ve Seç İletişim Kutusu

**Özellikler** penceresi, iletişim kutuları veya değişken Tasarımcısı gibi tasarımcılarda, bir veri türleri listesinden **türler için gözatma** ' yı seçtiğinizde, **bir .NET türü görüntüle ve Seç** iletişim kutusu (kısaltılmış bir biçimde "tür tarayıcısı" olarak adlandırılır) bulunur. Bu iletişim kutusunda, derlemelerin ve projelerin ağaç görünümünden bir tür seçebilirsiniz.

Bu iletişim kutusu, aşağıdakiler de dahil olmak üzere çeşitli Kullanıcı senaryolarında işe alındı:

- Bir değişkenin veya bağımsız değişkenin türü ayarlanırken.

- Genel etkinlik için bir tür seçerken.

- Etkinliğe bir catch eklenirken <xref:System.Activities.Statements.TryCatch> .

> [!NOTE]
> tür tarayıcısı Visual Basic basit dizi türleri görüntüleyebilir, ancak çok boyutlu dizi türleri gösterebilir. Ayrıntılar için bkz. [pürüzlü Diziler](/previous-versions/visualstudio/visual-studio-2008/hkhhsz9t(v=vs.90)) ve [çok boyutlu diziler](/previous-versions/visualstudio/visual-studio-2008/d2de1t93(v=vs.90)) .

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Tür tarayıcısından bir değer veya başvuru türü seçme

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Tür tarayıcısından bir değer veya başvuru türü seçmek için

1. **Tür adı** kutusuna, kullanmak istediğiniz türün adını girin.

2. Aşağıdakilerden birini yapın:

    - Kullanmak istediğiniz türün adı, **tür adı** kutusundaki ağaçta göründüğünde, seçmek için türe çift tıklayın.

    - Kullanmak istediğiniz türü benzersiz bir şekilde tanımlamak için **tür adı** kutusuna yeterli sayıda karakter yazın ve ardından türü seçmek için ENTER tuşuna basın

### <a name="to-select-a-generic-type-from-the-type-browser"></a>Tür tarayıcısından genel bir tür seçmek için

1. **Tür adı** kutusuna, kullanmak istediğiniz türün adını yazın.

2. Kullanmak istediğiniz türün adı **tür adı** kutusundaki ağaçta göründüğünde, açılan kutuların görünmesine neden olacak şekilde seçmek için türe tıklayın.

     Açılan kutulardan genel ' i kapatmak için kullanmak istediğiniz türü seçin ve ardından **Tamam**' a tıklayın.

## <a name="types-displayed-in-the-type-browser"></a>Tür tarayıcısında görünen türler

Tür tarayıcısında görünen türler, tür tarayıcısının nasıl başlatıldığına bağlı olarak farklılık gösterebilir. Tür tarayıcısı **VS2010** içindeki bir iş akışı projesinden başlatılmışsa, varsayılan olarak başvurulan derlemelerdeki tüm türler ve başvurulan projeler gösterilir. Tür tarayıcısı bir **VS2010** projesi sisteminin dışından (örneğin, yeniden barındırılan bir iş akışı uygulamasında veya tek başına bir iş akışı dosyasında) başlatılmışsa, varsayılan olarak, uygulama etki alanında yüklü derlemelerin tümünün türleri gösterilir.

Tür tarayıcısındaki türler, etkinlik Tasarımcısı geliştiricilerine göre filtrelenebilir. Belirli bir etkinlik için yalnızca türlerin bir alt kümesini görebilirsiniz. Örneğin, <xref:System.Activities.Statements.TryCatch> etkinliğinde, türü tarayıcıda yalnızca öğesinden türetilmiş türler <xref:System.Exception> gösterilir.

## <a name="filtering-search-results-in-the-type-browser"></a>Arama sonuçlarını tür tarayıcısında filtreleme

**Tür adı** kutusundaki türlerin listesi, bir eşleşme bulmak için daha fazla karakter yazdığınızda daha kısa olur. Yalnızca FullyQualified adı yazdığınız dize ile başlayan türler veya kısa adı yazdığınız dize ile başlayan ve filtrelenmiş listede görünen türler.

Örnek:

1. Yazma **işlemi** eşleşiyor <xref:System.OperationCanceledException> ancak eşleşmiyor <xref:System.InvalidOperationException> . Eşleştirmek için <xref:System.InvalidOperationException> , System. ı veya geçersiz yazmaya başlayın.

2. **Genel** eşleşmeler yazma <xref:System.GenericUriParser> , ancak <xref:System.Collections.Generic> ad alanındaki türler değil. Ad alanındaki türleri aramak için <xref:System.Collections.Generic> ad alanının tam adını yazın.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Tarayıcı türü iletişim kutusunu kullanarak bir hizmet sözleşmesi seçme

Bir hizmet sözleşmesi türü seçerken tür tarayıcısı yalnızca özniteliği olan türleri gösterir <xref:System.ServiceModel.ServiceContractAttribute> .

## <a name="see-also"></a>Ayrıca bkz.

- [Etkinlik Tasarımcılarını kullanma](control-flow-activity-designers.md)
