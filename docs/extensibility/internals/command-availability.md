---
title: Komut Kullanılabilirliği | Microsoft Dokümanlar
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dca47d9ed9968c101e3b6b859b51c1cd8d7404db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709692"
---
# <a name="command-availability"></a>Komut kullanılabilirliği

Visual Studio bağlamı hangi komutların kullanılabilir olduğunu belirler. Bağlam, geçerli projeye, geçerli düzenleyiciye, yüklenen VSPackages'e ve tümleşik geliştirme ortamının (IDE) diğer yönlerine bağlı olarak değişebilir.

## <a name="command-contexts"></a>Komut bağlamları

Aşağıdaki komut bağlamları en yaygın şunlardır:

- IDE: IDE tarafından sağlanan komutlar her zaman kullanılabilir.

- VSPackage: VSPackages komutları görüntülenecek veya gizli ne zaman tanımlayabilirsiniz.

- Proje: Proje komutları yalnızca şu anda seçili proje için görünür.

- Editör: Aynı anda yalnızca bir düzenleyici etkin olabilir. Etkin düzenleyicinin komutları kullanılabilir. Editör, bir dil hizmetiyle yakın çalışır. Dil hizmeti, komutlarını ilişkili düzenleyici bağlamında işlemelidir.

- Dosya türü: Düzenleyici birden fazla dosya türü yükleyebilir. Kullanılabilir komutlar dosya türüne bağlı olarak değişebilir.

- Etkin pencere: Son etkin belge penceresi, anahtar bağlamaları için kullanıcı arabirimi (UI) bağlamını ayarlar. Ancak, dahili web tarayıcısı benzer bir anahtar bağlama tablosu olan bir araç penceresi de UI bağlamını ayarlayabilirsiniz. HTML düzenleyicisi gibi çok sekmeli belge pencereleri için her sekmede farklı bir komut bağlamı GUID bulunur. Bir araç penceresi kaydedildikten sonra, **görünüm** menüsünde her zaman kullanılabilir.

- UI bağlamı: Arabirimi bağlamları, örneğin <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> çözüm <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> oluşturulurken veya <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> hata ayıklayıcı etkin olduğunda sınıfın değerleriyle tanımlanır. Birden çok Ara Bilgi bağlamı aynı anda etkin olabilir.

## <a name="define-custom-context-guids"></a>Özel bağlam GUID'leri tanımlama

Uygun bir komut bağlamı GUID zaten tanımlanmamışsa, VSPackage'ınızda bir tane tanımlayabilir ve komutlarınızın görünürlüğünü denetlemek için gerektiğinde etkin veya etkin olmaması için programlayabilirsiniz:

1. Yöntemi arayarak bağlam GUIDs kaydedin. <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A>

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> Yöntemi arayarak bir bağlam GUID durumunu alın.

3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> Yöntemi arayarak bağlam GUID'lerini açıp kapatın.

> [!CAUTION]
> VSPackage'ınızın varolan bağlam GUID'lerini etkilemediğinden emin olun, çünkü diğer VSPackage'lar bunlara bağlı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçim bağlamı nesneleri](../../extensibility/internals/selection-context-objects.md)
- [VSPackages kullanıcı arabirimi öğelerini nasıl ekler?](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
