---
title: Dil Hizmeti Filtreleri için Önemli Komutlar | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb29ee5b5a5359d6cfe34911656dfe9be015262e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707622"
---
# <a name="important-commands-for-language-service-filters"></a>Dil Hizmeti Filtreleri için Önemli Komutlar
Tam özellikli bir dil hizmeti filtresi oluşturmak istiyorsanız, aşağıdaki komutları işlemeyi düşünün. Komut tanımlayıcılarının tam listesi yönetilen kod için <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> numaralandırmada ve yönetilmeyen [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] kod için Stdidcmd.h üstbilgi dosyasında tanımlanır. Visual *Studio SDK kurulum yolu*\VisualStudioIntegration\Common\Inc. dosyasında Stdidcmd.h dosyasını bulabilirsiniz.

## <a name="commands-to-handle"></a>Ele Alınacak Komutlar

> [!NOTE]
> Aşağıdaki tablodaki her komut için filtre uygulama zorunlu değildir.

|Komut|Açıklama|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı sağ tıkladığında gönderilir. Bu komut, bir kısayol menüsü sağlamanın zamanının geldiğini gösterir. Bu komutu işlemezseniz, metin düzenleyicisi dile özgü komutlar olmadan varsayılan bir kısayol menüsü sağlar. Bu menüye kendi komutlarınızı eklemek için komutu işleyin ve kısayol menüsünü kendiniz görüntüleyin.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Genellikle kullanıcı CTRL+J yazdığında gönderilir. İfade <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> tamamlama kutusunu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> göstermek için yöntemi arayın.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı bir karakter yazdığında gönderilir. Tetikleyici karakterin ne zaman yazıldığında ne zaman yazıldığında ve sözdizimi boyama, ayraç eşleştirmeve hata işaretleri gibi deyim tamamlama, yöntem ipuçları ve metin işaretçileri sağlamak için bu komutu izleyin. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> İfade tamamlama yöntemini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ve yöntem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> ipuçları <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> için yöntemi arayın. Metin işaretçilerini desteklemek için, yazılan karakterin işaretçilerinizi güncelleştirmenizi gerektirip gerektirmediğini belirlemek için bu komutu izleyin.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı Enter tuşunu yazdığında gönderilir. Yöntem ucu penceresini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> ne zaman kapatacaklarını belirlemek için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>bu komutu izleyin. Varsayılan olarak, metin görünümü bu komutu işler.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı Arka Boşluk anahtarını yazdığında gönderilir. Yöntem deki yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>arayarak bir yöntem ipucu penceresinin ne zaman kapatılacağını belirlemek için monitör Varsayılan olarak, metin görünümü bu komutu işler.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Menüden veya kısayol tuşuyla gönderilir. Parametre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> bilgileriile <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ucu penceresini güncelleştirmek için yöntem arayın.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Kullanıcı bir değişkenin üzerinde gezindiğinde veya imleci bir değişkenüzerinde konumlandırdığında ve **Edit** menüsünde **IntelliSense'den** **Hızlı Bilgi'yi** seçtiğinde gönderilir. Bir ipucundaki değişkenin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> türünü, yöntemi 'nde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>çağırarak döndürün. Hata ayıklama etkinse, uç değişkenin değerini de göstermelidir.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Genellikle kullanıcı CTRL+SPACEBAR yazdığında gönderilir. Bu komut, dil hizmetine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>''de aramasını söyler.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Menüden gönderilen, genellikle **Edit** menüsünde **Gelişmiş'ten** **Yorum Seçimi** veya **YorumUn Artmama Seçimi.** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>kullanıcının seçili metni yorumlamak istediğini gösterir; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> kullanıcının seçili metnin yorumlarını geri almak istediğini gösterir. Bu komutlar yalnızca dil hizmeti tarafından uygulanabilir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)
