---
title: Komutla Aç'ı Kullanarak Dosyaları Görüntüleme | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708586"
---
# <a name="display-files-by-using-the-open-with-command"></a>Ile Aç komutunu kullanarak dosyaları görüntüleme
Proje, IDE'den **Açık** iletişim kutusunu görüntülemesini isteyebilir. Bu istek, kullanıcıdan standart düzenleyici seçkisi olan bir dosyayı açmasını ister. Aşağıdaki adımlar bu işlemi açıklar:

1. Proje, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> `OSE_UseOpenWithDialog` `OSEOpenDocEditor` parametre için bir değer belirterek çağırır.

2. Belgenin dosya adı uzantısına bağlı olarak, IDE kayıt defterinde listelenen hangi düzenleyicilerin belirtilen belgeyi açabileceğini belirler ve bu bilgileri **Açık iletişim** kutusunda görüntüler.

    > [!NOTE]
    > **Açık iletişim** kutusuna eklenmesi gereken içsel bir düzenleyicisi olan projelerin, bu tür her bir düzenleyici için bir düzenleyici fabrikası kaydetmesi gerekir. İçsel editörler yalnızca <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> yöntemin uygulanmasında uygulanan belirli bir proje türüyle birlikte çalışır. IDE çekirdek metin editörü ve ikili editör için yerleşik bir editör fabrikası vardır. IDE ayrıca, kayıtlı her Windows dosya ilişkilendirme adına bir düzenleyici fabrikası örneği oluşturur. Böyle bir dosyaya örnek olarak Microsoft Word'dür.

3. Kullanıcı iletişim **kutusuyla Aç'tan** bir öğe seçer seçmez, IDE daha <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> sonra arama yöntemini çağırarak belgeyi açar. Daha fazla bilgi için [bkz: Standart düzenleyicileri açın.](../../extensibility/how-to-open-standard-editors.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Proje öğelerini açma ve kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)
- [Dosya aç komutunu kullanarak dosyaları görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Nasıl yapılsın: Standart düzenleyicileri açın](../../extensibility/how-to-open-standard-editors.md)
