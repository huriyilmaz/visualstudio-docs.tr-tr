---
title: Komut Kullanılabilirliği | Microsoft Docs
description: Geçerli projeye, geçerli düzenleyiciye ve diğer faktörlere göre değişiklik yapılan komut bağlamının, komut bağlamında hangi komutların kullanılabilir olduğunu nasıl Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f2874909b772d6427dfa8869b203c1843f6ac153
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086878"
---
# <a name="command-availability"></a>Komut kullanılabilirliği

Aşağıdaki Visual Studio hangi komutların kullanılabilir olduğunu belirler. Bağlam geçerli projeye, geçerli düzenleyiciye, yüklenen VSPackage'lara ve tümleşik geliştirme ortamının (IDE) diğer yönlerine bağlı olarak değişebilir.

## <a name="command-contexts"></a>Komut bağlamları

En yaygın olan komut bağlamlarıdır:

- IDE: IDE tarafından sağlanan komutlar her zaman kullanılabilir.

- VSPackage: VSPackage'lar komutların ne zaman görüntü olacağını veya gizlen olacağını tanımlayabilir.

- Project: Project komutları yalnızca seçili olan proje için görünür.

- Düzenleyici: Aynı anda yalnızca bir düzenleyici etkin olabilir. Etkin düzenleyiciden komutlar kullanılabilir. Düzenleyici, dil hizmetiyle yakın bir şekilde çalışır. Dil hizmetinin komutlarını ilişkili düzenleyici bağlamında işlemesi gerekir.

- Dosya türü: Bir düzenleyici birden fazla dosya türü yükleyemedi. Kullanılabilir komutlar dosya türüne bağlı olarak değişebilir.

- Etkin pencere: Son etkin belge penceresi, anahtar bağlamaları için kullanıcı arabirimi (UI) bağlamını ayarlar. Ancak iç web tarayıcısına benzeyen bir anahtar bağlama tablosuna sahip bir araç penceresi de kullanıcı arabirimi bağlamını ayarlıyor olabilir. HTML düzenleyicisi gibi çok sekmeli belge pencerelerinin her sekmesinde farklı bir komut bağlamı GUID'si vardır. Bir araç penceresi kaydedildikten sonra görünüm menüsünde her **zaman** kullanılabilir.

- UI bağlamı: Ui bağlamları, örneğin çözümün ne zaman veya hata ayıklayıcı etkin olduğunda sınıfının <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> değerleriyle tanımlanır. Aynı anda birden çok kullanıcı arabirimi bağlamı etkin olabilir.

## <a name="define-custom-context-guids"></a>Özel bağlam GUID'lerini tanımlama

Uygun bir komut bağlamı GUID'si önceden tanımlanmamışsa, VSPackage içinde bir tane tanımlayabilir ve komutlarının görünürlüğünü kontrol etmek için gerektiğinde etkin veya etkin değil olarak programlayarak:

1. yöntemini çağırarak bağlam GUID'lerini <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> kaydetme.

2. yöntemini çağırarak bağlam GUID'lerinin durumunu <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> elde.

3. yöntemini çağırarak bağlam GUID'lerini açma ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> kapatma.

> [!CAUTION]
> Diğer VSPackage'lar bağımlı olduğundan VSPackage'nizin mevcut bağlam GUID'lerini etkilemey olduğundan emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçim bağlamı nesneleri](../../extensibility/internals/selection-context-objects.md)
- [VSPackage'lar kullanıcı arabirimi öğelerini nasıl ekler?](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
