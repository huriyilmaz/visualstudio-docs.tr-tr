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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659170"
---
# <a name="choose-operation-dialog-box-legacy"></a>İşlem Seç İletişim Kutusu (Eski)
Bu konu başlığı altında, eski ' de **Işlem seçme** iletişim kutusunun nasıl kullanılacağı açıklanmaktadır [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Ya da ' i hedefliyorsanız, eski kullanın [!INCLUDE[wfd2](../includes/wfd2-md.md)] [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 **Işlem Seç** iletişim kutusu, bir <xref:System.Workflow.Activities.ReceiveActivity> aktiviteyle veya etkinlikle ilişkilendirilecek bir işlem seçmek için kullanılır <xref:System.Workflow.Activities.SendActivity> . Bu etkinliklerle bu iletişim kutusunu kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: WCF sözleşme Işlemi uygulama (eski)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) ve [nasıl yapılır: WCF sözleşme Işlemini çağırma (eski)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).

 Aşağıdaki tabloda, **Işlem Seç** iletişim kutusunun kullanıcı ARABIRIMI (UI) öğeleri açıklanmaktadır.

|Arabirim Öğesi|Description|
|----------------|-----------------|
|**Sözleşme Ekle**|Sizin için yeni bir sözleşme oluşturur. Bu sözleşmede yeni işlemler tanımlayabilirsiniz. (Bu yalnızca ile kullanılır <xref:System.Workflow.Activities.ReceiveActivity> .)|
|**Işlem Ekle**|**Işlem Seç** iletişim kutusunda oluşturduğunuz yeni bir sözleşmeye yeni işlemler ekler. **Note:**  Yalnızca **Işlem Seç** iletişim kutusu aracılığıyla oluşturduğunuz sözleşmelere yeni işlemler ekleyebilirsiniz. <br /><br /> (Bu yalnızca ile kullanılır <xref:System.Workflow.Activities.ReceiveActivity> .)|
|**İçeri Aktar...**|Önceden tanımlanmış bir sözleşmeyi içeri aktarır ve bu sözleşmeden bir işlem seçmenizi sağlar.|
|**İşlem adı**|Şu anda seçili olan işlemin adı. Bu metin kutusu, yalnızca **Işlem Seç** iletişim kutusu aracılığıyla bir işlem oluşturduysanız düzenlenebilir.|
|**Parametreler**|Seçili olan işlem için parametre tanımlarını içeren sekme. **Note:**  Parametre tanımları yalnızca **Işlem Seç** iletişim kutusu aracılığıyla bir işlem oluşturduysanız değiştirilebilir.|
|**Özellikler**|<xref:System.Net.Security.ProtectionLevel>İstemci ve hizmet arasında gönderilen iletiler için ayarları içeren sekme. **Note:**  Bu sekme yalnızca **Işlem Seç** iletişim kutusu aracılığıyla bir işlem oluşturduysanız etkindir.|
|**İzinler**|<xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> Bu işlemi çağırmaya izin verilen kullanıcıların ve özelliklerini içeren sekme. Örneğin, yalnızca Yöneticiler grubundaki kullanıcıların bu işlemi çağırmasını izin veriliyorsa, **rol** metin kutusuna "Yöneticiler" yazın.<br /><br /> Bu sekme, **ChooseOperation** iletişim kutusu ve **içeri aktarma** düğmesi aracılığıyla içeri aktarılan işlemler için oluşturulan her iki işlem için de etkinleştirilir.|

> [!NOTE]
> **Işlem Seç** iletişim kutusu yalnızca iş akışındaki diğer etkinlikler tarafından kullanılan sözleşmeleri veya işlemleri gösterir <xref:System.Workflow.Activities.SendActivity> . Benzer şekilde, etkinlikler için **Işlem Seç** iletişim kutusu, <xref:System.Workflow.Activities.ReceiveActivity> yalnızca Iş akışındaki diğer **ReceiveActivity** etkinlikleri tarafından kullanılan sözleşmeleri veya işlemleri gösterir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: WCF sözleşme Işlemi uygulama (eski)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) [nasıl yapılır: WCF sözleşme Işlemini çağırma (eskı)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) [Windows Workflow Foundation UI Yardımı için eski tasarımcı](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)