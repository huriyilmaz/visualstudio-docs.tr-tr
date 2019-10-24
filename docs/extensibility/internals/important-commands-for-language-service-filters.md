---
title: Dil hizmeti filtreleri için önemli komutlar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0e2e605a0725c2f88922d3e3ce899263171bc4d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726924"
---
# <a name="important-commands-for-language-service-filters"></a>Dil Hizmeti Filtreleri için Önemli Komutlar
Tam özellikli bir dil hizmeti filtresi oluşturmak istiyorsanız aşağıdaki komutları işlemeyi göz önünde bulundurun. Komut tanımlayıcılarının tam listesi, yönetilen kod için <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> numaralandırmasında ve yönetilmeyen [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] kodu için Stdidcmd. h üstbilgi dosyasında tanımlanmıştır. Stdidcmd. h dosyasını *Visual STUDIO SDK yükleme yolu*\VisualStudioIntegration\Common\Inc. ' de bulabilirsiniz.

## <a name="commands-to-handle"></a>Işlenecek komutlar

> [!NOTE]
> Aşağıdaki tabloda her komutun filtreleneceği zorunlu değildir.

|Komut|Açıklama|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı sağ tıkladığı zaman gönderilir. Bu komut, bir kısayol menüsü sağlamak için zaman olduğunu gösterir. Bu komutu tutamadıysanız, metin düzenleyici dile özgü komutlar olmadan varsayılan bir kısayol menüsü sağlar. Bu menüye kendi komutlarınızı eklemek için, komutu işleyin ve kendiniz bir kısayol menüsü görüntüleyin.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Genellikle kullanıcı CTRL + J yazdığında gönderilir. Deyimin tamamlanma kutusunu göstermek için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> yöntemi çağırın.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı bir karakter yazdığında gönderilir. Bir tetikleyici karakterinin ne zaman yazıldığı ve ifade tamamlama, yöntem ipuçları ve sözdizimi renklendirme, küme ayracı eşleştirme ve hata işaretçileri gibi metin işaretçileri sağlamak için bu komutu izleyin. For ifadesinin tamamlanması için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> yöntemi ve yöntem ipuçları için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> yöntemi çağırın. Metin işaretçilerini desteklemek için, yazılan karakterin işaretçilerin güncelleştirilmesini gerektirip gerektirmediğini öğrenmek için bu komutu izleyin.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı Enter tuşunu yazdığında gönderilir. @No__t_1 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> yöntemini çağırarak bir yöntem ipucu penceresinin ne zaman durdurulacağını öğrenmek için bu komutu izleyin. Varsayılan olarak, metin görünümü bu komutu işler.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı geri al anahtarını yazdığında gönderilir. @No__t_1 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> yöntemini çağırarak bir yöntem ipucu penceresinin ne zaman durdurulacağını belirleme İzleyicisi. Varsayılan olarak, metin görünümü bu komutu işler.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Bir menü veya kısayol anahtarından gönderilir. İpucu penceresini parametre bilgileriyle güncelleştirmek için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> yöntemi çağırın.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı bir değişkenin üzerine gittiğinde veya imleci bir değişkende konumlandırdığında veya **Düzenle** menüsünde **IntelliSense** 'den **hızlı bilgi** ' yı seçtiğinde gönderilir. @No__t_1 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> yöntemini çağırarak bir ipucunda değişkenin türünü döndürün. Hata ayıklama etkinse, ipucu değişkenin değerini de göstermelidir.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Genellikle kullanıcı CTRL + Ara çubuğu yazdığında gönderilir. Bu komut, dil hizmetinin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> yöntemini çağırmasını söyler.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Bir menüden gönderilir, genellikle **düzenleme** menüsünde Seçimi Açıklama **veya** **Gelişmiş** ' i Açıklama Ekle ' yi **seçerek** . <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>, kullanıcının seçili metni açıklama eklemek istediğini belirtir;  <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>, kullanıcının seçili metinde açıklama eklemek istediğini gösterir. Bu komutlar yalnızca dil hizmeti tarafından uygulanabilir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)