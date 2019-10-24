---
title: Kullanıcı arabirimi güncelleştiriliyor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf41a41e68aa73e07bdcafe8bcdcd335fff6e6eb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718794"
---
# <a name="updating-the-user-interface"></a>Kullanıcı Arabirimini Güncelleştirme
Bir komut uyguladıktan sonra, Kullanıcı arabirimini yeni komutlarınızın durumuyla güncelleştirmek için kod ekleyebilirsiniz.

 Tipik bir Win32 uygulamasında, komut kümesi sürekli olarak yoklanabilir ve Kullanıcı bunları görüntülediğinde tek tek komutların durumu ayarlanabilir. Ancak, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kabuğu sınırsız sayıda VSPackages barındırabildiğinden, kapsamlı yoklama, özellikle de yönetilen kod ve COM arasındaki birlikte çalışma derlemelerinde yoklama hızını düşürebilir.

### <a name="to-update-the-ui"></a>Kullanıcı arabirimini güncelleştirmek için

1. Aşağıdaki adımlardan birini uygulayın:

    - <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> yöntemini çağırın.

         Bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> arabirimi, <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> hizmetinden aşağıdaki gibi elde edilebilir.

        ```csharp
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)
        {
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));
            if (vsShell != null)
            {
                int hr = vsShell.UpdateCommandUI(0);
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);
            }
        }

        ```

         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> parametresi sıfır olmayan (`TRUE`), güncelleştirme zaman uyumlu olarak ve anında gerçekleştirilir. İyi performans sağlanmasına yardımcı olması için bu parametre için sıfır (`FALSE`) geçişi yapmanızı öneririz. Önbelleğe almayı önlemek istiyorsanız,. vsct dosyasında komutu oluştururken `DontCache` bayrağını uygulayın. Bununla birlikte, bu bayrağı dikkatli bir şekilde kullanın veya performans azalabilir. Komut bayrakları hakkında daha fazla bilgi için bkz. [komut bayrağı öğe](../extensibility/command-flag-element.md) belgeleri.

    - Bir pencerede yerinde etkinleştirme modelini kullanarak bir ActiveX denetimi barındıran VSPackages içinde, <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> yönteminin kullanımı daha uygun olabilir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> arabirimindeki <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> yöntemi ve <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> arabirimindeki <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> yöntemi işlevsel olarak eşdeğerdir. Her ikisi de ortamın tüm komutların durumunu yeniden sorgulayamasına neden olur. Genellikle, bir güncelleştirme hemen gerçekleştirilmez. Bunun yerine, bir güncelleştirme, boşta kalma süresine kadar gecikir. Kabuk, iyi performans sağlanmasına yardımcı olması için komut durumunu önbelleğe alır. Önbelleğe almayı önlemek istiyorsanız,. vsct dosyasında komutu oluştururken `DontCache` bayrağını uygulayın. Yine de, performans azalabileceğinden, bu bayrağı dikkatle kullanın.

         <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> arabirimini, bir <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> nesnesi üzerinde `QueryInterface` yöntemini çağırarak veya <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> hizmetinden arabirimini alarak elde edebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Uygulama](../extensibility/internals/command-implementation.md)