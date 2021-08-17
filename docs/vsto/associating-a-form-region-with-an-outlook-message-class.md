---
title: Form bölgelerini bir form Outlook sınıfıyla ilişkilendirme
description: Form bölgelerini her öğenin ileti Microsoft Office Outlook bir form bölgesi görüntülemektedir.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.InvalidMessageClassName
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FormRegionMessageClassAttribute
- form regions [Office development in Visual Studio], message classes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f38640840b929b4044ca37d6571c82289f32b55f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038233"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Form bölgelerini bir form Outlook sınıfıyla ilişkilendirme
  Form bölgelerini her Microsoft Office Outlook ileti sınıfıyla bağarak, form bölgelerini hangi öğelerin görüntüle olduğunu belirtebilirsiniz. Örneğin, bir posta öğesinin en altına bir form bölgesi eklemek için form bölgelerini ileti sınıfıyla `IPM.Note` ilişkilendirilebilirsiniz.

 Bir form bölgelerini bir ileti sınıfıyla ilişkilendirmek için, **New Outlook Form** Bölgesi sihirbazında ileti sınıfı adını belirtin veya form bölgesi fabrika sınıfına bir öznitelik uygulama.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="understand-outlook-message-classes"></a>İleti Outlook sınıflarını anlama
 Bir Outlook sınıfı, bir öğe türü Outlook tanımlar. Aşağıdaki tabloda, bu sekiz standart öğe türü ve bunların ileti sınıfı adları listele.

|Outlook Öğe Türü|İleti Sınıfı Adı|
|-----------------------|------------------------|
|AppointmentItem|`IPM.Appointment`|
|ContactItem|`IPM.Contact`|
|DistListItem|`IPM.DistList`|
|JournalItem|`IPM.Activity`|
|MailItem|`IPM.Note`|
|PostItem|`IPM.Post` veya `IPM.Post.RSS`|
|Taskıtem|`IPM.Task`|

 Özel ileti sınıflarının adlarını da belirtebilirsiniz. Özel ileti sınıfları, özel formlarda tanımladığınız özel formları Outlook.

> [!NOTE]
> Değiştirme ve tüm form bölgelerini değiştirme için yeni bir özel ileti sınıfı adı belirtebilirsiniz. Mevcut bir özel formun ileti sınıfı adını kullanmak zorunda değildir. Özel ileti sınıfının adı benzersiz olmalıdır. Adın benzersiz olmasını sağlamak için aşağıdakine benzer bir adlandırma kuralı kullanmak gerekir: \<*StandardMessageClassName*> . \<*Company*> .\<*MessageClassName*> (örneğin: `IPM.Note.Contoso.MyMessageClass` ).

## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Form bölgelerini bir form Outlook sınıfıyla ilişkilendirme
 Form bölgelerini ileti sınıfıyla ilişkilendirmenin iki yolu vardır:

- Yeni **Form Outlook sihirbazını** kullanın.

- Sınıf özniteliklerini uygulama.

### <a name="use-the-new-outlook-form-region-wizard"></a>Yeni Form Outlook sihirbazını kullanma
 Yeni Form Bölgesi **sihirbazının Outlook** sayfasında, standart ileti sınıflarını seçin ve form bölgesiyle ilişkilendirmek istediğiniz özel ileti sınıflarının adlarını yazın.

 Form bölgesi formun tamamını veya varsayılan sayfasını değiştirmek için tasarlanmışsa standart ileti sınıfları kullanılamaz. Standart ileti sınıfı adlarını yalnızca bir forma yeni sayfa ekli veya formun en altına eklenen formlar için belirtebilirsiniz. Daha fazla bilgi [için, bkz. How to: Add-in Outlook form bölgesi ekleme.](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)

 Bir veya daha fazla özel ileti sınıfı eklemek için adlarını Bu form bölgesi hangi özel **ileti sınıflarını görüntüler? kutusuna** yazın.

 Yazarak adlar aşağıdaki yönergelere uygun olmalıdır:

- Tam ileti sınıfı adını kullanın (örneğin: "IPM. Note.Contoso").

- Birden çok ileti sınıfı adı ayırmak için noktalı virgül kullanın.

- "IPM Outlook gibi standart ileti sınıfları dahil değildir. Not" veya "IPM. İletişime geçin". Yalnızca "IPM. Note.Contoso".

- Temel ileti sınıfını tek başına belirtme (örneğin: "IPM").

- Her ileti sınıfı adı için 256 karakteri aşmayın.

  Yeni **Outlook Form Bölgesi** sihirbazı, Son'a tıklarken giriş biçiminizi **doğrular.**

> [!NOTE]
> Yeni **Outlook Form Bölgesi** sihirbazı, sizin için ileti sınıfı adlarının doğru veya geçerli olduğunu doğrulamaz.

 Sihirbazı tamamlasanız, **Yeni Outlook Form** Bölgesi sihirbazı, belirtilen ileti sınıfı adlarını içeren form bölgesi sınıfına öznitelikler uygular. Bu öznitelikleri el ile de uygulayabilirsiniz.

### <a name="apply-class-attributes"></a>Sınıf özniteliklerini uygulama
 Yeni Form Bölgesi sihirbazını tamamlandıktan sonra Outlook bir form bölgesi ile **bir Outlook sınıfını ilişkilendirilebilirsiniz.** Bunu yapmak için, form bölgesi fabrika sınıfına öznitelikleri uygulama.

 Aşağıdaki örnek adlı <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> bir form bölgesi fabrika sınıfına uygulanmış iki özniteliği `myFormRegion` gösterir. İlk öznitelik, form bölgelerini bir posta iletisi formu için standart ileti sınıfıyla ilişkilendirmektedir. İkinci öznitelik, form bölgelerini adlı özel bir ileti sınıfıyla `IPM.Task.Contoso` ilişkilendirmektedir.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs" id="Snippet1":::

 Öznitelikler aşağıdaki yönergelere uygun olmalıdır:

- Özel ileti sınıfları için, tam ileti sınıfı adını kullanın (örneğin: "IPM. Note.Contoso").

- Temel ileti sınıfını tek başına belirtme (örneğin: "IPM").

- Her ileti sınıfı adı için 256 karakteri aşmayın.

- Form bölgesi formun tamamının veya formun varsayılan sayfasının yerini alıyorsa standart ileti sınıflarının adlarını dahil edin. Standart ileti sınıfı adlarını yalnızca bir forma yeni sayfa ekli veya formun en altına eklenen formlar için belirtebilirsiniz. Daha fazla bilgi [için, bkz. How to: Add-in Outlook form bölgesi ekleme.](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)

  Visual Studio, projeyi derlemek için ileti sınıfı adlarının biçimini doğrular.

> [!NOTE]
> Visual Studio, ileti sınıfı adlarının doğru veya geçerli olduğunu doğrulamaz.

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında form bölgelerine erişme](../vsto/accessing-a-form-region-at-run-time.md)
- [Form Outlook bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Adım adım kılavuz: Form Outlook tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Form bölgelerini Outlook yönergeleri](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Form adı ve ileti sınıfına genel bakış](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)
- [Formlar Outlook öğeleri birlikte nasıl çalışır?](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)
