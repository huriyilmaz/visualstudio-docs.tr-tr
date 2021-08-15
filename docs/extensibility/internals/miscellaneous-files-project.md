---
title: Çeşitli dosyalar Project | Microsoft Docs
description: Visual Studio projesindeki dosyaları açmak için kullanılabilecek iki düzenleyici türü hakkında bilgi edinin ve hangi düzenleyiciyi kullanacağınızı belirleyen proje rolü.
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
ms.openlocfilehash: 2a3c372e80b9c0843d63c1ed6e674cf9cc5c1bb6d1d68bec4f6fa1e06b4476dc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121337896"
---
# <a name="miscellaneous-files-project"></a>Çeşitli Dosyalar Projesi
Bir kullanıcı proje öğelerini açtığında, IDE çeşitli dosyalar projesine bir çözümdeki projelerin üyesi olmayan tüm öğeleri atar.

 Projeler, bir Kullanıcı bir proje öğesi açtığında hangi düzenleyicinin kullanıldığını belirlemek için önemli bir rol oynar. Bir proje, belirli dosyaları projeye özgü bir düzenleyici veya standart bir düzenleyici kullanılarak açılacak şekilde tasarlanabilir.

 Projeye özgü bir düzenleyici, genellikle kullanıcının özel bilgiye sahip olmasını veya projeden özel arabirimler kullanmasını gerektirir. Daha fazla bilgi için bkz. [nasıl yapılır: Project-Specific düzenleyicileri açma](../../extensibility/how-to-open-project-specific-editors.md).

 Standart bir düzenleyici, herhangi bir projede belirli bir uzantının herhangi bir dosyasını açabilir. Kullanıcı, projeler için metin Düzenleyicisi gibi bazı standart düzenleyicileri özelleştirebilir, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ancak yine de ortak karakterlerini koruyabilir. Standart düzenleyiciler yöntemi kullanılarak oluşturulur <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .

 Çözümdeki hiçbir proje bir proje öğesi açabildiğinden yanıt verirse, IDE, herhangi bir dosyayı açan çeşitli dosyalar projesi adlı özel bir proje sağlar.

 Bu özel proje, bir dosyanın bir proje bağlamı dışında açılmasını sağlar. Yöntemin işlenmesi sırasında <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> , Miscellaneous Files projesi her zaman çok düşük bir önceliğe sahip olarak yanıt verir. Bu nedenle, çeşitli dosyalar projesi her zaman dosyaları açan daha yüksek öncelikli bir projeye üretir.

 çeşitli dosyalar projesi, kullanıcının **yeni Project** iletişim kutusuyla açıkça oluşturmasını gerektirmez. Ayrıca, Miscellaneous Files projesi Proje üyelerinin bir listesini kalıcı olarak yönetmez. Her Kullanıcı için en son kullanılan dosyaların listesini kaydetmek için isteğe bağlı bir özellik kullanır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Nasıl Yapılır: Projeye Özgü Düzenleyicileri Açma](../../extensibility/how-to-open-project-specific-editors.md)
- [Nasıl Yapılır: Standart Düzenleyicileri Açma](../../extensibility/how-to-open-standard-editors.md)
- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
