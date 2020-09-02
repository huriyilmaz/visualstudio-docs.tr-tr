---
title: Dil hizmeti filtreleri için önemli komutlar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 03bb20abf32f7c320ed56f4a649a9f43453e7694
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64819857"
---
# <a name="important-commands-for-language-service-filters"></a>Dil Hizmeti Filtreleri için Önemli Komutlar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tam özellikli bir dil hizmeti filtresi oluşturmak istiyorsanız aşağıdaki komutları işlemeyi göz önünde bulundurun. Komut tanımlayıcılarının tam listesi, <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> yönetilen kod için numaralandırmada ve yönetilmeyen kod Için Stdidcmd. h üst bilgi dosyasına tanımlanmıştır [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] . Stdidcmd. h dosyasını *Visual STUDIO SDK yükleme yolu*\VisualStudioIntegration\Common\Inc. ' de bulabilirsiniz.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski Dil Hizmeti Geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)
