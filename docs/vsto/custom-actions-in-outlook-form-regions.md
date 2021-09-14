---
title: Outlook form bölgelerinde özel eylemler
description: yanıtla ve yanıtla gibi eylem görüntüleme düğmelerinin nasıl yapıldığını öğrenin, kullanıcıların bir Microsoft Office Outlook öğeye yanıt vermesini sağlar.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 75fcc83dc06a9503b5ab1571315dc95028734446
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725604"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Outlook form bölgelerinde özel eylemler
  eylemler, kullanıcıların bir Microsoft Office Outlook öğeye yanıt vermesini sağlayan düğmeleri görüntüler. Örneğin, bir posta öğesine yanıt vermek için, kullanıcılar **Yanıtla**, **Tümünü Yanıtla** veya **İleri git** düğmelerine tıklayın. Bu eylemlerin her biri yeni bir posta öğesi oluşturur ve özgün öğeden alınan bilgileri kullanarak öğenin alanlarını doldurur.

 her türlü Outlook öğesi açan özel bir eylem oluşturabilirsiniz. Örneğin, yeni bir randevu veya görev öğesi açan özel bir eylem ekleyebilirsiniz. Özel bir eylemin özelliklerini ayarlayın veya yeni öğenin alanlarını doldurmak için özel kod kullanın. özel eylemler, bir Outlook denetçisi penceresinde açık olan bir öğenin **özel eylemler** açılan penceresinde görünür.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-custom-actions-to-a-form-region"></a>Form bölgesine özel eylemler ekleme
 Form bölgesine özel eylem eklemek için **özel eylemler** iletişim kutusunu kullanın. **Çözüm Gezgini** içindeki Form bölgesini seçip **özellikler penceresinde** **bildirim** düğümünü genişleterek, **customactions** özelliğini seçerek ve ardından üç nokta düğmesine (![ASP.NET mobile designer elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil tasarımcı elips")) tıklayarak **özel eylemler** iletişim kutusunu açabilirsiniz.

 Bir *hedef form* belirtmek Için **özel eylemler** iletişim kutusunu kullanabilirsiniz. Hedef form, Kullanıcı özel eylemi çalıştırdığında görünen formdur.

 **Özel eylemler** iletişim kutusunu ayrıca, özgün öğeden gelen bilgilerin hedef formda görünmesini nasıl istediğinizi belirtmek için de kullanabilirsiniz.

 Aşağıdaki tabloda, **özel eylemler** iletişim kutusunda kullanılabilen özellikler açıklanmaktadır.

|Özellik|Açıklama|
|--------------|-----------------|
|**AddressLike**|Hedef formun nasıl giderilecektir belirtir.|
|**Gövde**|Özgün öğenin gövdesinin hedef forma nasıl ekleneceğini belirtir.|
|**Etkin**|Özel eylemin etkin olup olmadığını gösterir. Bu özellik **false** olarak ayarlandıysa, özel eylem devre dışıdır.|
|**Yöntem**|Özel eylem yürütüldüğünde kullanılabilir yanıt türünü belirtir. Özel eylem formu gönderebilir, formu açabilir veya formu göndermek ya da açmak isteyip istemedikleri konusunda kullanıcıyı uyarır.|
|**Ad**|Koddaki bu özel eyleme başvurmak için kullanabileceğiniz dahili adı belirtir.|
|**ShowOnRibbon**|Özel eylemin orijinal öğenin şeridinde görüntülenip görüntülenmeyeceğini gösterir.|
|**SubjectPrefix**|Hedef formun konu satırının başlangıcına eklenen metni belirtir.|
|**TargetForm**|Hedef formun ileti sınıfı adını belirtir. Örneğin, IPM yazın **.** Görev formunu açmak için görev.|
|**Başlık**|Özel eylem düğmesinin etiketini belirtir.|

## <a name="customize-a-custom-action-at-run-time"></a>Çalışma zamanında özel bir eylemi özelleştirme
 Ayrıca, kod kullanarak özel eyleme davranış ekleyebilirsiniz. Örneğin, e-posta alıcılarının adlarını alan ve bu adları yeni bir randevu öğesine katılımcı olarak ekleyen bir kod ekleyebilirsiniz. Bunu yapmak için, [MailItem nesnesinin](/office/vba/api/Outlook.MailItem) [CustomAction](/office/vba/api/Outlook.MailItem.CustomAction) olayını işleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [izlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [form bölgesini Outlook ileti sınıfıyla ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
