---
title: Open with Command komutunu kullanarak dosyaları | Microsoft Docs
description: Bir projenin dosyaları görüntülemek için tümleşik geliştirme ortamına (IDE) Visual Studio Birlikte Aç komutunu nasıl çağırabilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1930f643ee609ad101c13a7103a2c7253e7588b2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725086"
---
# <a name="display-files-by-using-the-open-with-command"></a>Birlikte Aç komutunu kullanarak dosyaları görüntüleme
Proje, IDE'den Birlikte Aç iletişim **kutusunu görüntülemesini** sorabilir. Bu istek, kullanıcıdan çeşitli standart düzenleyiciler olan bir dosyayı açması istenir. Aşağıdaki adımlar bu işlemi açıklar:

1. Proje, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> parametresi için değerini belirterek `OSE_UseOpenWithDialog` `OSEOpenDocEditor` çağrısında bulundu.

2. Belgenin dosya adı uzantısına bağlı olarak, IDE kayıt defterinde listelenen düzenleyicilerin belirtilen belgeyi açalarını belirler ve bu bilgileri Birlikte Aç **iletişim** kutusunda görüntüler.

    > [!NOTE]
    > Birlikte Aç iletişim kutusuna dahil edilecek iç düzenleyiciye  sahip projeler, bu tür düzenleyicilerin her biri için bir düzenleyici fabrikası kaydetmeli. Iç düzenleyiciler yalnızca yöntemin uygulanmasında zorlanan belirli bir proje türüyle birlikte <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> işlev gösterir. IDE, çekirdek metin düzenleyicisi ve ikili düzenleyici için yerleşik bir düzenleyici fabrikasına sahip. IDE ayrıca her kayıtlı dosya ilişkilendirmesi adına bir düzenleyici fabrikası Windows oluşturur. Bu tür bir dosyaya örnek olarak Microsoft Word.

3. Kullanıcı Birlikte Aç iletişim kutusundan  bir öğe seçer seçmez IDE, yöntemini çağırarak belgeyi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> açar. Daha fazla bilgi için, [bkz. How to: Open standard editors](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Proje öğelerini açma ve kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)
- [Dosya Aç komutunu kullanarak dosyaları görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Nasıl: Standart düzenleyicileri açma](../../extensibility/how-to-open-standard-editors.md)
