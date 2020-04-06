---
title: Çeşitli Dosyalar Projesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95cc1312fb7b381e1e20df834698480295fadcc8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707093"
---
# <a name="miscellaneous-files-project"></a>Çeşitli Dosyalar Projesi
Bir kullanıcı proje öğelerini açtığında, IDE Çeşitli Dosyalar'a bir çözümdeki herhangi bir projeye üye olmayan öğeleri projeye atar.

 Projeler, bir kullanıcı bir proje öğesini açtığında hangi düzenleyicinin kullanıldığını belirlemede önemli bir rol oynar. Proje, projeye özgü bir düzenleyici veya standart bir düzenleyici kullanarak belirli dosyaları açmak üzere tasarlanabilir.

 Projeye özel bir düzenleyici genellikle kullanıcının özel bilgiye sahip olması veya projeden özel arabirimler kullanmasını gerektirir. Daha fazla bilgi için [bkz: Projeye Özel Düzenleyicileri Açın.](../../extensibility/how-to-open-project-specific-editors.md)

 Standart bir düzenleyici, herhangi bir projede belirli bir uzantının herhangi bir dosyayı açabilir. Kullanıcı, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] metin düzenleyicisi gibi bazı standart düzenleyicileri projeler için özelleştirebilir, ancak yine de ortak karakterini koruyabilir. Standart editörler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> yöntem kullanılarak oluşturulur.

 Çözümdeki hiçbir proje bir proje öğesini açabileceği yanıtını vermiyorsa, IDE herhangi bir dosyayı açan Çeşitli Dosyalar projesi adlı özel bir proje sağlar.

 Bu özel proje, bir projenin bağlamı dışında bir dosyanın açılmasını sağlar. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> Yöntemin işlenmesi sırasında, Çeşitli Dosyalar projesi her zaman çok düşük bir öncelikle yanıt verir. Bu nedenle, Çeşitli Dosyalar projesi her zaman dosyaları açabilen daha yüksek öncelikli herhangi bir projeye verim verir.

 Çeşitli Dosyalar projesi, kullanıcının **yeni proje** iletişim kutusuyla açıkça oluşturmasını gerektirmez. Ayrıca, Çeşitli Dosyalar projesi kalıcı olarak proje üyelerinin listesini yönetmez. Her kullanıcı için en son kullanılan dosyaların listesini kaydetmek için isteğe bağlı bir özellik kullanır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Nasıl Yapılır: Projeye Özgü Düzenleyicileri Açma](../../extensibility/how-to-open-project-specific-editors.md)
- [Nasıl Yapılır: Standart Düzenleyicileri Açma](../../extensibility/how-to-open-standard-editors.md)
- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
