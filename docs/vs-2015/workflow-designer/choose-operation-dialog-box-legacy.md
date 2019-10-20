---
title: Işlem Seç Iletişim kutusu (eski) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f2736db7e18733a9477238cafad21088eb135e89
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659170"
---
# <a name="choose-operation-dialog-box-legacy"></a>İşlem Seç İletişim Kutusu (Eski)
Bu konu başlığı altında, eski [!INCLUDE[wfd1](../includes/wfd1-md.md)] **Işlem seçme** iletişim kutusunun nasıl kullanılacağı açıklanmaktadır. @No__t_1 veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] hedeflemek gerektiğinde eski [!INCLUDE[wfd2](../includes/wfd2-md.md)] kullanın.

 **Işlem Seç** iletişim kutusu, bir <xref:System.Workflow.Activities.ReceiveActivity> etkinliğiyle veya <xref:System.Workflow.Activities.SendActivity> etkinlikiyle ilişkilendirilecek bir işlem seçmek için kullanılır. Bu etkinliklerle bu iletişim kutusunu kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: WCF sözleşme Işlemi uygulama (eski)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) ve [nasıl yapılır: WCF sözleşme Işlemini çağırma (eski)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).

 Aşağıdaki tabloda, **Işlem Seç** iletişim kutusunun kullanıcı ARABIRIMI (UI) öğeleri açıklanmaktadır.

|Arabirim Öğesi|Açıklama|
|----------------|-----------------|
|**Sözleşme Ekle**|Sizin için yeni bir sözleşme oluşturur. Bu sözleşmede yeni işlemler tanımlayabilirsiniz. (Bu yalnızca <xref:System.Workflow.Activities.ReceiveActivity> ile kullanılır.)|
|**Işlem Ekle**|**Işlem Seç** iletişim kutusunda oluşturduğunuz yeni bir sözleşmeye yeni işlemler ekler. **Note:**  Yalnızca **Işlem Seç** iletişim kutusu aracılığıyla oluşturduğunuz sözleşmelere yeni işlemler ekleyebilirsiniz. <br /><br /> (Bu yalnızca <xref:System.Workflow.Activities.ReceiveActivity> ile kullanılır.)|
|**İçeri Aktar...**|Önceden tanımlanmış bir sözleşmeyi içeri aktarır ve bu sözleşmeden bir işlem seçmenizi sağlar.|
|**İşlem adı**|Şu anda seçili olan işlemin adı. Bu metin kutusu, yalnızca **Işlem Seç** iletişim kutusu aracılığıyla bir işlem oluşturduysanız düzenlenebilir.|
|**Parametreler**|Seçili olan işlem için parametre tanımlarını içeren sekme. **Note:**  Parametre tanımları yalnızca **Işlem Seç** iletişim kutusu aracılığıyla bir işlem oluşturduysanız değiştirilebilir.|
|**Veri Erişimi**|İstemci ve hizmet arasında gönderilen iletiler için <xref:System.Net.Security.ProtectionLevel> ayarlarını içeren sekme. **Note:**  Bu sekme yalnızca **Işlem Seç** iletişim kutusu aracılığıyla bir işlem oluşturduysanız etkindir.|
|**İzinler**|Bu işlemi çağırmaya izin verilen kullanıcıların <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> ve <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> özelliklerini içeren sekme. Örneğin, yalnızca Yöneticiler grubundaki kullanıcıların bu işlemi çağırmasını izin veriliyorsa, **rol** metin kutusuna "Yöneticiler" yazın.<br /><br /> Bu sekme, **ChooseOperation** iletişim kutusu ve **içeri aktarma** düğmesi aracılığıyla içeri aktarılan işlemler için oluşturulan her iki işlem için de etkinleştirilir.|

> [!NOTE]
> **Işlem Seç** iletişim kutusu yalnızca iş akışındaki diğer <xref:System.Workflow.Activities.SendActivity> etkinlikleri tarafından kullanılan sözleşmeleri veya işlemleri gösterir. Benzer şekilde, <xref:System.Workflow.Activities.ReceiveActivity> etkinlikler için **Işlem Seç** iletişim kutusu, yalnızca iş akışındaki diğer **ReceiveActivity** etkinlikleri tarafından kullanılan sözleşmeleri veya işlemleri gösterir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: WCF sözleşme Işlemi uygulama (eski)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) [nasıl yapılır: WCF sözleşme Işlemini çağırma (eskı)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) [Windows Workflow Foundation UI Yardımı için eski tasarımcı](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)