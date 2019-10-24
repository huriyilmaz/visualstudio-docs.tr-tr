---
title: Çeşitli dosyalar projesi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c46126507ef9bb293bd0fa6771f53343ad6206f7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726687"
---
# <a name="miscellaneous-files-project"></a>Çeşitli Dosyalar Projesi
Bir kullanıcı proje öğelerini açtığında, IDE çeşitli dosyalar projesine bir çözümdeki projelerin üyesi olmayan tüm öğeleri atar.

 Projeler, bir Kullanıcı bir proje öğesi açtığında hangi düzenleyicinin kullanıldığını belirlemek için önemli bir rol oynar. Bir proje, belirli dosyaları projeye özgü bir düzenleyici veya standart bir düzenleyici kullanılarak açılacak şekilde tasarlanabilir.

 Projeye özgü bir düzenleyici, genellikle kullanıcının özel bilgiye sahip olmasını veya projeden özel arabirimler kullanmasını gerektirir. Daha fazla bilgi için bkz. [nasıl yapılır: projeye özgü düzenleyicilerin açık](../../extensibility/how-to-open-project-specific-editors.md)olması.

 Standart bir düzenleyici, herhangi bir projede belirli bir uzantının herhangi bir dosyasını açabilir. Kullanıcı, projeler için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] metin Düzenleyicisi gibi bazı standart düzenleyicileri özelleştirebilir, ancak yine de ortak karakterlerini koruyabilir. Standart düzenleyiciler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> yöntemi kullanılarak oluşturulur.

 Çözümdeki hiçbir proje bir proje öğesi açabildiğinden yanıt verirse, IDE, herhangi bir dosyayı açan çeşitli dosyalar projesi adlı özel bir proje sağlar.

 Bu özel proje, bir dosyanın bir proje bağlamı dışında açılmasını sağlar. @No__t_0 yönteminin işlenmesi sırasında, Miscellaneous Files projesi her zaman çok düşük bir önceliğe sahip olarak yanıt verir. Bu nedenle, çeşitli dosyalar projesi her zaman dosyaları açan daha yüksek öncelikli bir projeye üretir.

 Çeşitli dosyalar projesi, kullanıcının bunu **Yeni proje** iletişim kutusuyla açıkça oluşturmasını gerektirmez. Ayrıca, Miscellaneous Files projesi Proje üyelerinin bir listesini kalıcı olarak yönetmez. Her Kullanıcı için en son kullanılan dosyaların listesini kaydetmek için isteğe bağlı bir özellik kullanır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Nasıl Yapılır: Projeye Özgü Düzenleyicileri Açma](../../extensibility/how-to-open-project-specific-editors.md)
- [Nasıl Yapılır: Standart Düzenleyicileri Açma](../../extensibility/how-to-open-standard-editors.md)
- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)