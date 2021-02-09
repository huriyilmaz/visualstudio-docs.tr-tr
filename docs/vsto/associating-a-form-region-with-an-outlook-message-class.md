---
title: Form bölgesini Outlook ileti sınıfıyla ilişkilendirme
description: Form bölgesini her bir öğenin ileti sınıfıyla ilişkilendirerek, hangi Microsoft Office Outlook öğelerinin form bölgesi görüntülemesini istediğinizi nasıl kullanabileceğinizi öğrenin.
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
ms.workload:
- office
ms.openlocfilehash: 0bbbd381ff84714b780bbb817ccfea64ac05e949
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882550"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Form bölgesini Outlook ileti sınıfıyla ilişkilendirme
  Form bölgesini her öğenin ileti sınıfıyla ilişkilendirerek, hangi Microsoft Office Outlook öğelerinin form bölgesi görüntülemesini belirtebilirsiniz. Örneğin, bir posta öğesinin altına bir form bölgesi eklemek istiyorsanız, form bölgesini `IPM.Note` ileti sınıfıyla ilişkilendirebilirsiniz.

 Form bölgesini bir ileti sınıfıyla ilişkilendirmek için, **Yeni Outlook form bölgesi** Sihirbazı 'nda ileti sınıfı adını belirtin veya bir özniteliği form bölgesi fabrikası sınıfına uygulayın.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="understand-outlook-message-classes"></a>Outlook ileti sınıflarını anlayın
 Outlook ileti sınıfı bir Outlook öğesi türünü tanımlar. Aşağıdaki tabloda, bu sekiz standart öğe türü ve onların ileti sınıfı adları listelenmektedir.

|Outlook öğesi türü|İleti sınıfı adı|
|-----------------------|------------------------|
|Randevutmentıtem|`IPM.Appointment`|
|Kişi kimliği|`IPM.Contact`|
|DistListItem|`IPM.DistList`|
|JournalItem|`IPM.Activity`|
|MailItem|`IPM.Note`|
|Potıtem|`IPM.Post` veya `IPM.Post.RSS`|
|TaskItem|`IPM.Task`|

 Özel ileti sınıflarının adlarını da belirtebilirsiniz. Özel ileti sınıfları, Outlook 'ta tanımladığınız özel formları tanımlar.

> [!NOTE]
> Değiştirme ve değiştirme form bölgelerinde yeni bir özel ileti sınıfı adı belirtebilirsiniz. Mevcut bir özel formun ileti sınıfı adını kullanmanız gerekmez. Özel ileti sınıfının adı benzersiz olmalıdır. Adın benzersiz olduğundan emin olmanın bir yolu aşağıdakine benzer bir adlandırma kuralı kullanmaktır: \<*StandardMessageClassName*> . \<*Company*> .\<*MessageClassName*> (örneğin: `IPM.Note.Contoso.MyMessageClass` ).

## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Form bölgesini Outlook ileti sınıfıyla ilişkilendirme
 Form bölgesini ileti sınıfıyla ilişkilendirmenin iki yolu vardır:

- **Yeni Outlook form bölgesi** Sihirbazı 'nı kullanın.

- Sınıf özniteliklerini uygulayın.

### <a name="use-the-new-outlook-form-region-wizard"></a>Yeni Outlook form bölgesi Sihirbazı 'nı kullanma
 **Yeni Outlook form bölgesi** Sihirbazı ' nın son sayfasında, standart ileti sınıfları ' nı seçebilir ve form bölgesiyle ilişkilendirmek istediğiniz özel ileti sınıflarının adlarını yazabilirsiniz.

 Form bölgesi formun tamamını veya formun varsayılan sayfasını değiştirecek şekilde tasarlanmışsa standart ileti sınıfları kullanılamaz. Yalnızca bir forma yeni bir sayfa ekleyen veya formun alt kısmına eklenen formlar için standart ileti sınıfı adlarını belirtebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

 Bir veya daha fazla özel ileti sınıfı eklemek için, **Bu form bölgesini hangi özel ileti sınıflarının görüntüleyeceği?** kutusunu yazın.

 Yazdığınız adlar aşağıdaki kılavuzlarla uyumlu olmalıdır:

- Tam olarak nitelenmiş ileti sınıfı adını kullanın (örneğin: "ıPM. Note. contoso ").

- Birden çok ileti sınıfı adını ayırmak için noktalı virgül kullanın.

- "IPM" gibi standart Outlook ileti sınıflarını eklemeyin. Note "veya" ıPM. İletişim kurun. Yalnızca "ıPM" gibi özel ileti sınıflarını dahil edin. Note. contoso ".

- Temel ileti sınıfını kendi belirtmeyin (örneğin: "ıPM").

- Her ileti sınıfı adı için 256 karakteri aşmayın.

  **Yeni Outlook form bölgesi** Sihirbazı, **son**' a tıkladığınızda giriş biçiminizi doğrular.

> [!NOTE]
> **Yeni Outlook form bölgesi** Sihirbazı, sağladığınız ileti sınıfı adlarının doğru veya geçerli olduğunu doğrulamaz.

 Sihirbazı tamamladığınızda, **Yeni Outlook form bölgesi** Sihirbazı öznitelikleri, belirtilen ileti sınıfı adlarını içeren form bölgesi sınıfına uygular. Ayrıca, bu öznitelikleri el ile de uygulayabilirsiniz.

### <a name="apply-class-attributes"></a>Sınıf özniteliklerini Uygula
 **Yeni Outlook form bölgesi** Sihirbazı 'nı tamamladıktan sonra bir form bölgesini Outlook ileti sınıfıyla ilişkilendirebilirsiniz. Bunu yapmak için, öznitelikleri form bölgesi fabrikası sınıfına uygulayın.

 Aşağıdaki örnek, <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> adlı bir form bölgesi fabrikası sınıfına uygulanmış olan iki özniteliği gösterir `myFormRegion` . İlk öznitelik, form bölgesini posta iletisi formu için standart bir ileti sınıfıyla ilişkilendirir. İkinci öznitelik, form bölgesini adlı özel bir ileti sınıfıyla ilişkilendirir `IPM.Task.Contoso` .

 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]

 Öznitelikler aşağıdaki kılavuzlarla uyumlu olmalıdır:

- Özel ileti sınıfları için tam olarak nitelenmiş ileti sınıfı adını kullanın (örneğin: "ıPM. Note. contoso ").

- Temel ileti sınıfını kendi belirtmeyin (örneğin: "ıPM").

- Her ileti sınıfı adı için 256 karakteri aşmayın.

- Form bölgesi formun tamamını veya formun varsayılan sayfasını değiştirirse standart ileti sınıflarının adlarını eklemeyin. Yalnızca bir forma yeni bir sayfa ekleyen veya formun alt kısmına eklenen formlar için standart ileti sınıfı adlarını belirtebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

  Visual Studio, projeyi oluştururken ileti sınıfı adlarının biçimini doğrular.

> [!NOTE]
> Visual Studio, sağladığınız ileti sınıfı adlarının doğru veya geçerli olduğunu doğrulamaz.

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında form bölgesine erişme](../vsto/accessing-a-form-region-at-run-time.md)
- [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [İzlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Outlook form bölgeleri oluşturma yönergeleri](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Form adı ve ileti sınıfına genel bakış](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)
- [Outlook Forms ve öğelerinin birlikte çalışması](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)
