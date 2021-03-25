---
title: Dil hizmeti filtreleri için önemli komutlar | Microsoft Docs
description: Visual Studio 'da tam özellikli dil hizmeti filtresi oluştururken desteklemeniz gereken önemli komutlar hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5d27f1c3057266d1b167999f3178a3e554a78ddb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069562"
---
# <a name="important-commands-for-language-service-filters"></a>Dil Hizmeti Filtreleri için Önemli Komutlar
Tam özellikli bir dil hizmeti filtresi oluşturmak istiyorsanız aşağıdaki komutları işlemeyi göz önünde bulundurun. Komut tanımlayıcılarının tam listesi, <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> yönetilen kod için numaralandırmada ve yönetilmeyen kod Için Stdidcmd. h üst bilgi dosyasına tanımlanmıştır [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] . Stdidcmd. h dosyasını *Visual STUDIO SDK yükleme yolu*\VisualStudioIntegration\Common\Inc. ' de bulabilirsiniz.

## <a name="commands-to-handle"></a>Işlenecek komutlar

> [!NOTE]
> Aşağıdaki tabloda her komutun filtreleneceği zorunlu değildir.

|Komut|Açıklama|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı sağ tıkladığı zaman gönderilir. Bu komut, bir kısayol menüsü sağlamak için zaman olduğunu gösterir. Bu komutu tutamadıysanız, metin düzenleyici dile özgü komutlar olmadan varsayılan bir kısayol menüsü sağlar. Bu menüye kendi komutlarınızı eklemek için, komutu işleyin ve kendiniz bir kısayol menüsü görüntüleyin.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Genellikle kullanıcı CTRL + J yazdığında gönderilir. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Deyimin tamamlanma kutusunu göstermek için üzerinde yöntemini çağırın.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı bir karakter yazdığında gönderilir. Bir tetikleyici karakterinin ne zaman yazıldığı ve ifade tamamlama, yöntem ipuçları ve sözdizimi renklendirme, küme ayracı eşleştirme ve hata işaretçileri gibi metin işaretçileri sağlamak için bu komutu izleyin. For <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ifadesinin tamamlanmasında yöntemini ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> for yöntemi ipuçları üzerindeki yöntemi çağırın. Metin işaretçilerini desteklemek için, yazılan karakterin işaretçilerin güncelleştirilmesini gerektirip gerektirmediğini öğrenmek için bu komutu izleyin.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı Enter tuşunu yazdığında gönderilir. Metodu üzerinde yöntemini çağırarak bir yöntem ipucu penceresinin ne zaman durdurulacağını öğrenmek için bu komutu izleyin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> . Varsayılan olarak, metin görünümü bu komutu işler.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı geri al anahtarını yazdığında gönderilir. Yöntemi ' de çağırarak bir yöntem ipucu penceresinin ne zaman durdurulacağını belirleme İzleyicisi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> . Varsayılan olarak, metin görünümü bu komutu işler.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Bir menü veya kısayol anahtarından gönderilir. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> İpucu penceresini parametre bilgileriyle güncelleştirmek için üzerinde yöntemini çağırın.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı bir değişkenin üzerine gittiğinde veya imleci bir değişkende konumlandırdığında veya **Düzenle** menüsünde **IntelliSense** 'den **hızlı bilgi** ' yı seçtiğinde gönderilir. Üzerinde metodunu çağırarak, değişkenin türünü bir ipucunda döndürün <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . Hata ayıklama etkinse, ipucu değişkenin değerini de göstermelidir.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Genellikle kullanıcı CTRL + Ara çubuğu yazdığında gönderilir. Bu komut, dil hizmetinin üzerinde yöntemini çağırmasını söyler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Bir menüden gönderilir, genellikle **düzenleme** menüsünde Seçimi Açıklama **veya** **Gelişmiş** ' i Açıklama Ekle ' yi **seçerek** . <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> kullanıcının seçili metni açıklama eklemek istediğini belirtir; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> kullanıcının seçili metinde açıklama eklemek istediğini belirtir. Bu komutlar yalnızca dil hizmeti tarafından uygulanabilir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)
