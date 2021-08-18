---
title: Çeşitli Dosyalar Project | Microsoft Docs
description: Bir Visual Studio projesinde dosyaları açmak için kullanılan iki düzenleyici türü ve kullanılacak düzenleyicinin belirlenmesinde projenin rolü hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ff3643d3a1f2d48b0fac071f57738d73055529e7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057258"
---
# <a name="miscellaneous-files-project"></a>Çeşitli Dosyalar Projesi
Kullanıcı proje öğelerini açtığında, IDE Çözümdeki herhangi bir projenin üyesi olan öğelerden herhangi birini Çeşitli Dosyalar projesine atar.

 Projeler, kullanıcı bir proje öğesini açtığında hangi düzenleyicinin kullanılı olduğunu belirlemede önemli bir rol oynar. Proje, projeye özgü bir düzenleyici veya standart bir düzenleyici kullanarak belirli dosyaları açmak için tasar kullanılabilir.

 Projeye özgü bir düzenleyici genellikle kullanıcının özel bilgiye sahip olması veya projeden özel arabirimler kullanması gerekir. Daha fazla bilgi için, [bkz. How to: Open Project-Specific Editors](../../extensibility/how-to-open-project-specific-editors.md).

 Standart düzenleyici herhangi bir projede belirli bir uzantının herhangi bir dosyasını açabilir. Kullanıcı, projeler için metin düzenleyicisi gibi bazı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] standart düzenleyicileri özelleştirilebilir ancak yine de genel karakterini koruyabilirsiniz. Standart düzenleyiciler yöntemi kullanılarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> oluşturulur.

 Çözümde herhangi bir proje, bir proje öğesini açamıyorsa, IDE herhangi bir dosyayı açan Çeşitli Dosyalar projesi adlı özel bir proje sağlar.

 Bu özel proje, bir dosyanın proje bağlamı dışında açılmasını sağlar. yönteminin işlemesi sırasında, Çeşitli Dosyalar projesi her zaman çok düşük <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> öncelikli olarak yanıt verir. Bu nedenle, Çeşitli Dosyalar projesi her zaman dosyaları açan herhangi bir yüksek öncelikli projeye yol açar.

 Çeşitli Dosyalar projesi, kullanıcının Bunu Yeni Dosyalar iletişim kutusuyla **açıkça Project** gerektirmez. Ayrıca, Çeşitli Dosyalar projesi proje üyelerinin listesini kalıcı olarak yönetmez. Her kullanıcı için en son kullanılan dosyaların listesini kaydetmek için isteğe bağlı bir özellik kullanır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Nasıl Yapılır: Projeye Özgü Düzenleyicileri Açma](../../extensibility/how-to-open-project-specific-editors.md)
- [Nasıl Yapılır: Standart Düzenleyicileri Açma](../../extensibility/how-to-open-standard-editors.md)
- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
