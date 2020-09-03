---
title: Birlikte Aç komutunu kullanarak dosyaları görüntüleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4051793077e613981e1dd5b44f1736878f5853e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708586"
---
# <a name="display-files-by-using-the-open-with-command"></a>Birlikte Aç komutunu kullanarak dosyaları görüntüleme
Bir proje IDE 'nin **birlikte Aç** iletişim kutusunu görüntülemesini isteyebilir. Bu istek, kullanıcıdan standart düzenleyiciler seçimine sahip bir dosyayı açmasını ister. Aşağıdaki adımlarda bu işlem açıklanır:

1. Proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , parametresi için bir değer belirterek çağırır `OSE_UseOpenWithDialog` `OSEOpenDocEditor` .

2. Belgenin dosya adı uzantısına bağlı olarak IDE, kayıt defterinde listelenen düzenleyicilerin belirtilen belgeyi açabildiğini belirler ve bu bilgileri **birlikte Aç** iletişim kutusunda görüntüler.

    > [!NOTE]
    > **Birlikte Aç** iletişim kutusuna dahil olması gereken bir iç düzenleyiciye sahip olan projeler, her bir düzenleyici için bir düzenleyici fabrikası kaydetmelidir. İç düzenleyiciler yalnızca belirli bir proje türüyle birlikte çalışır ve bu yöntem, yöntemi uygulamasında zorlanır <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> . IDE, çekirdek metin Düzenleyicisi ve ikili düzenleyici için yerleşik bir düzenleyici fabrikası içerir. IDE, kayıtlı her Windows dosya ilişkilendirmesi adına bir düzenleyici fabrikası örneği de oluşturur. Bu tür bir dosyaya örnek olarak Microsoft Word vardır.

3. Kullanıcı **birlikte Aç** iletişim kutusundan bir öğe SEÇTIĞINDE, IDE yöntemi çağırarak belgeyi açar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> . Daha fazla bilgi için bkz. [nasıl yapılır: standart düzenleyiciler açma](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Proje öğelerini aç ve Kaydet](../../extensibility/internals/opening-and-saving-project-items.md)
- [Dosya Aç komutunu kullanarak dosyaları görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Nasıl yapılır: standart düzenleyiciler açma](../../extensibility/how-to-open-standard-editors.md)
