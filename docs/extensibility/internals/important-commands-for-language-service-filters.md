---
title: Dil Hizmeti Filtreleri için Önemli Komutlar | Microsoft Docs
description: Visual Studio'da tam özellikli bir dil hizmeti filtresi oluştururken desteklemeniz gereken önemli komutlar hakkında Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 995cc17117f695500115a918ed24efc447855340dcb37e6b1dff8f9efa23638e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388636"
---
# <a name="important-commands-for-language-service-filters"></a>Dil Hizmeti Filtreleri için Önemli Komutlar
Tam özellikli bir dil hizmeti filtresi oluşturmak için aşağıdaki komutları işlemeyi göz önünde bulundurabilirsiniz. Komut tanımlayıcılarının tam listesi, yönetilen kod için numaralandırma ve yönetilemeyen kod <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> için Stdidcmd.h üst bilgi dosyasında [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] tanımlanır. Stdidcmd.h dosyasını *VISUAL STUDIO SDK* yükleme yolu \VisualStudioIntegration\Common\Inc yolunda bulabilirsiniz.

## <a name="commands-to-handle"></a>Ele Gereken Komutlar

> [!NOTE]
> Aşağıdaki tabloda yer alan her komutu filtrelemek zorunlu değildir.

|Komut|Açıklama|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı sağ tıkladığında gönderilir. Bu komut, bir kısayol menüsü sağlamanın zamanı olduğunu gösterir. Bu komutu işlemezsiniz, metin düzenleyicisi dile özgü komutlar olmadan varsayılan bir kısayol menüsü sağlar. Bu menüye kendi komutlarınızı eklemek için komutu işin ve bir kısayol menüsünü kendiniz açın.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Genellikle kullanıcı CTRL+J tuşlarına basarken gönderilir. deyimi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> tamamlanma kutusunu göstermek <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> için üzerinde yöntemini çağırma.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı bir karakter gönderdiği zaman gönderilir. Bir tetikleyici karakterinin ne zaman yazılmış olduğunu belirlemek ve deyim tamamlama, yöntem ipuçları ve söz dizimi renklendirme, küme ayracı eşleştirme ve hata işaretçileri gibi metin işaretçileri sağlamak için bu komutu izleyin. for deyimi tamamlaması üzerinde yöntemini ve yöntem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> ipuçları için üzerinde yöntemini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> çağırma. Metin işaretçilerini desteklemek için, yazılmış karakterin işaretçilerinizi güncelleştirmenizi gerektirip gerektir olmadığını belirlemek için bu komutu izleyebilirsiniz.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı Enter tuşuna basınca gönderilir. üzerinde yöntemini çağırarak bir yöntem ipucu penceresinin ne zaman kapatın, belirlemek <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> için bu komutu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> izleyebilirsiniz. Varsayılan olarak, metin görünümü bu komutu işler.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı Geri Al anahtarını gönderdiği zaman gönderilir. üzerinde yöntemini çağırarak bir yöntem ipucu penceresinin ne zaman <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> kapatın, belirlemek için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> izleyici. Varsayılan olarak, metin görünümü bu komutu işler.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Bir menüden veya kısayol anahtarından gönderilir. İpucu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> penceresini parametre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> bilgileriyle güncelleştirmek için üzerinde yöntemini çağırma.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı bir değişkenin üzerine geldiğinde veya imleci bir değişkenin  üzerine yerleştirdiğinde ve Düzenle menüsünde **IntelliSense'den** Hızlı Bilgi'yi **seçerek** gönderilir. üzerinde yöntemini çağırarak bir ipucunda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> değişkeninin türünü <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> dönüş. Hata ayıklama etkinse, ipucu değişkenin değerini de gösterse gerekir.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Genellikle kullanıcı CTRL+ARA ÇUBUĞU tuşlarına basarken gönderilir. Bu komut, dil hizmetine üzerinde yöntemini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> çağırmasını <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> söyler.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Genellikle Düzenle menüsündeki Gelişmiş **menüsünden** Açıklama **Seçimi veya** Açıklama Seçimini **Kaldır menüsünden** gönderilir.  <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> kullanıcının seçilen metni açıklama olarak almak istediğini gösterir; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> , kullanıcının seçilen metni yorumdan almak istediğini gösterir. Bu komutlar yalnızca dil hizmeti tarafından kullanılabilir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)
