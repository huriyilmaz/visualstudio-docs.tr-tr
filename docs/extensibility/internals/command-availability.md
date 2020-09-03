---
title: Komut kullanılabilirliği | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709692"
---
# <a name="command-availability"></a>Komut kullanılabilirliği

Visual Studio bağlamı hangi komutların kullanılabilir olduğunu belirler. Bağlam geçerli projeye, geçerli düzenleyiciye, yüklenen VSPackages ve tümleşik geliştirme ortamının (IDE) diğer yönlerini bağlı olarak değişebilir.

## <a name="command-contexts"></a>Komut bağlamları

Aşağıdaki komut bağlamları en yaygın olarak verilmiştir:

- IDE: IDE tarafından sağlanan komutlar her zaman kullanılabilir.

- VSPackage:, komutların ne zaman görüntüleneceğini veya gizlendiğini tanımlayabilir.

- Proje: proje komutları yalnızca şu anda seçili proje için görünür.

- Düzenleyici: tek seferde yalnızca bir düzenleyici etkin olabilir. Etkin düzenleyiciden komutlar var. Bir düzenleyici, dil hizmetiyle yakından birlikte çalışmaktadır. Dil hizmeti, komutlarını ilişkili düzenleyicinin bağlamında işlemelidir.

- Dosya türü: bir düzenleyici, birden fazla dosya türü yükleyebilir. Kullanılabilir komutlar dosya türüne bağlı olarak değişebilir.

- Etkin pencere: son etkin belge penceresi, anahtar bağlamaları için Kullanıcı arabirimi (UI) bağlamını ayarlar. Ancak, iç Web tarayıcısına benzer bir anahtar bağlama tablosuna sahip bir araç penceresi de UI bağlamını ayarlayabilir. HTML Düzenleyicisi gibi çok sekmeli belge pencereleri için her sekmenin farklı bir komut bağlamı GUID 'i vardır. Bir araç penceresi kaydedildikten sonra, **Görünüm** menüsünde her zaman kullanılabilir.

- UI bağlamı: UI bağlamları, sınıf değerleri tarafından tanımlanır <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> , örneğin, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> çözüm derlenmekte veya <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> hata ayıklayıcı etkin olduğunda. Aynı anda birden çok UI bağlamı etkin olabilir.

## <a name="define-custom-context-guids"></a>Özel bağlam GUID 'Leri tanımla

Uygun bir komut bağlamı GUID 'SI zaten tanımlanmamışsa, VSPackage içinde bir tane tanımlayabilir ve ardından komutlarınızın görünürlüğünü denetlemek için gerektiğinde etkin veya devre dışı olarak programlayabilirsiniz:

1. Metodu çağırarak bağlam GUID 'Lerini kaydettirin <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> .

2. Yöntemini çağırarak bağlam GUID 'inin durumunu alın <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> .

3. Yöntemini çağırarak bağlam GUID 'Lerini açın ve kapatın <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> .

> [!CAUTION]
> Diğer VSPackages bunlara bağlı olabileceğinden VSPackage 'ın var olan herhangi bir bağlam GUID 'i etkilemediğinden emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçim bağlamı nesneleri](../../extensibility/internals/selection-context-objects.md)
- [VSPackages Kullanıcı arabirimi öğeleri ekleme](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
