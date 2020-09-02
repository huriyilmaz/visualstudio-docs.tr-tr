---
title: Outlook form bölgelerindeki özel eylemler
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 817cf9fe8698c2908e873246a8971f90fe72b460
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71254450"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Outlook form bölgelerindeki özel eylemler
  Eylemler, kullanıcıların bir Microsoft Office Outlook öğesine yanıt vermesini sağlayan düğmeleri görüntüler. Örneğin, bir posta öğesine yanıt vermek için, kullanıcılar **Yanıtla**, **Tümünü Yanıtla**veya **İleri git** düğmelerine tıklayın. Bu eylemlerin her biri yeni bir posta öğesi oluşturur ve özgün öğeden alınan bilgileri kullanarak öğenin alanlarını doldurur.

 Herhangi bir tür Outlook öğesini açan özel bir eylem oluşturabilirsiniz. Örneğin, yeni bir randevu veya görev öğesi açan özel bir eylem ekleyebilirsiniz. Özel bir eylemin özelliklerini ayarlayın veya yeni öğenin alanlarını doldurmak için özel kod kullanın. Özel Eylemler, bir Outlook Inspector penceresinde açık olan bir öğenin **özel eylemler** açılan penceresinde görünür.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-custom-actions-to-a-form-region"></a>Form bölgesine özel eylemler ekleme
 Form bölgesine özel eylem eklemek için **özel eylemler** iletişim kutusunu kullanın. **Çözüm Gezgini**Içindeki form bölgesini seçip **Özellikler penceresinde** **bildirim** düğümünü genişleterek, **CustomActions** özelliğini seçerek ve ardından üç nokta düğmesine (![ASP.net Mobile Designer elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer elips")) tıklayarak **özel eylemler** iletişim kutusunu açabilirsiniz.

 Bir *hedef form*belirtmek Için **özel eylemler** iletişim kutusunu kullanabilirsiniz. Hedef form, Kullanıcı özel eylemi çalıştırdığında görünen formdur.

 **Özel eylemler** iletişim kutusunu ayrıca, özgün öğeden gelen bilgilerin hedef formda görünmesini nasıl istediğinizi belirtmek için de kullanabilirsiniz.

 Aşağıdaki tabloda, **özel eylemler** iletişim kutusunda kullanılabilen özellikler açıklanmaktadır.

|Özellik|Açıklama|
|--------------|-----------------|
|**AddressLike**|Hedef formun nasıl giderilecektir belirtir.|
|**Gövde**|Özgün öğenin gövdesinin hedef forma nasıl ekleneceğini belirtir.|
|**Etkin**|Özel eylemin etkin olup olmadığını gösterir. Bu özellik **false**olarak ayarlandıysa, özel eylem devre dışıdır.|
|**Yöntem**|Özel eylem yürütüldüğünde kullanılabilir yanıt türünü belirtir. Özel eylem formu gönderebilir, formu açabilir veya formu göndermek ya da açmak isteyip istemedikleri konusunda kullanıcıyı uyarır.|
|**Ad**|Koddaki bu özel eyleme başvurmak için kullanabileceğiniz dahili adı belirtir.|
|**ShowOnRibbon**|Özel eylemin orijinal öğenin şeridinde görüntülenip görüntülenmeyeceğini gösterir.|
|**SubjectPrefix**|Hedef formun konu satırının başlangıcına eklenen metni belirtir.|
|**TargetForm**|Hedef formun ileti sınıfı adını belirtir. Örneğin, IPM yazın **. ** Görev formunu açmak için görev.|
|**Başlık**|Özel eylem düğmesinin etiketini belirtir.|

## <a name="customize-a-custom-action-at-run-time"></a>Çalışma zamanında özel bir eylemi özelleştirme
 Ayrıca, kod kullanarak özel eyleme davranış ekleyebilirsiniz. Örneğin, e-posta alıcılarının adlarını alan ve bu adları yeni bir randevu öğesine katılımcı olarak ekleyen bir kod ekleyebilirsiniz. Bunu yapmak için, [MailItem nesnesinin](/office/vba/api/Outlook.MailItem) [CustomAction](/office/vba/api/Outlook.MailItem.CustomAction) olayını işleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [İzlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Form bölgesini Outlook ileti sınıfıyla ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
