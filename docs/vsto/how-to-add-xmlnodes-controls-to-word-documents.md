---
title: 'Nasıl yapılır: Word belgelerine XMLNodes denetimleri ekleme'
description: yinelenen bir XML şeması öğesini Microsoft Office bir Word belgesiyle eşleştirdiğinizde Visual Studio otomatik olarak belgenize bir XMLNodes denetimi ekler.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 69320f9734951bae3af6a4bf5447302435db1541
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122858"
---
# <a name="how-to-add-xmlnodes-controls-to-word-documents"></a>Nasıl yapılır: Word belgelerine XMLNodes denetimleri ekleme
  **Önemli** bu konu başlığı altında Microsoft Word, microsoft, Microsoft Word 'den özel XML ile ilgili belirli işlevlerin bir uygulamasını kaldırdıkları zaman, Birleşik Devletler ve bölgeleri dışında bulunan Microsoft Word veya 2010 microsoft tarafından lisanslanan ürünlerin ve kuruluşların kullanımı ve kullanımı için özel olarak sunulur. Microsoft Word ile ilgili bu bilgiler, Birleşik Devletler veya şirket içinde çalışan ya da şirket içinde çalışan veya Microsoft tarafından lisanslanan Microsoft Word, 10 ocak 2010 ' den sonra lisanslı ürünleri kullanan bireyler veya kuruluşlar tarafından okunamaz veya kullanılmıyor olabilir. Bu ürünler, bu tarihten önce lisanslanan ürünlerle aynı veya satın alınmadan ve Birleşik Devletler dışında kullanılmak üzere lisanslanmaz.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 yinelenen bir XML şeması öğesini Microsoft Office bir Word belgesiyle eşleştirdiğinizde, Visual Studio otomatik olarak <xref:Microsoft.Office.Tools.Word.XMLNodes> belgenize bir denetim ekler.

 Tekrarlamayan XML şeması öğelerini eşleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Word belgelerine XmlNode denetimleri ekleme](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).

> [!NOTE]
> <xref:Microsoft.Office.Tools.Word.XMLNodes>Denetim, **araç kutusu** veya **veri kaynakları** penceresinde kullanılamaz veya program aracılığıyla oluşturulabilir.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnodes-control-to-a-document"></a>Bir belgeye XMLNodes denetimi eklemek için

1. Visual Studio tasarımcısının belgesinde, şeritte, **geliştirici** sekmesine tıklayın.

    > [!NOTE]
    > **Geliştirici** sekmesi görünür değilse, önce onu göstermelisiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

2. **XML** grubunda, **şema**' ya tıklayın.

     **Şablonlar ve eklentiler** iletişim kutusu açılır.

3. **XML şeması** sekmesine tıklayın.

4. **Şema ekle**' ye tıklayın.

     **Şema ekle** iletişim kutusu açılır.

5. Yinelenen şema öğelerini içeren bir XML şeması seçin ve **Aç**' a tıklayın.

     **şema Ayarlar** iletişim kutusu görüntülenir.

6. Bir diğer ad atayın veya şemayı bir diğer ad olmadan eklemek için **Tamam 'a** tıklayın.

     Şema, **şema ekle** iletişim kutusuna eklenir.

7. **Şema ekle** Iletişim kutusunda **Tamam**' a tıklayın.

     **XML yapısı** görev bölmesi açılır.

8. Belgeye eklemek için **XML yapısı** görev bölmesinde yinelenen şema öğesine tıklayın.

     Bir <xref:Microsoft.Office.Tools.Word.XMLNodes> Denetim oluşturulup projeye eklenir.

## <a name="see-also"></a>Ayrıca bkz.
- [XMLNodes denetimi](../vsto/xmlnodes-control.md)
- [Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
