---
title: Kullanıcı arabirimi güncelleştiriliyor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c51ae790eb35645fbe9aec5d9c422e1051aaa69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698884"
---
# <a name="updating-the-user-interface"></a>Kullanıcı Arabirimini Güncelleştirme
Bir komut uyguladıktan sonra, Kullanıcı arabirimini yeni komutlarınızın durumuyla güncelleştirmek için kod ekleyebilirsiniz.

 Tipik bir Win32 uygulamasında, komut kümesi sürekli olarak yoklanabilir ve Kullanıcı bunları görüntülediğinde tek tek komutların durumu ayarlanabilir. Ancak, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kabuk sınırsız sayıda VSPackages barındırabildiğinden, kapsamlı bir yoklama, özellikle yönetilen kod ve com arasındaki birlikte çalışma derlemelerinin üzerinde yoklama hızını düşürebilir.

### <a name="to-update-the-ui"></a>Kullanıcı arabirimini güncelleştirmek için

1. Aşağıdaki adımlardan birini uygulayın:

    - Yöntemini çağırın <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> .

         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>Aşağıdaki şekilde hizmetten bir arabirim elde edilebilir <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> .

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

         Parametresinin parametresi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> sıfır ( `TRUE` ) ise, güncelleştirme zaman uyumlu ve anında gerçekleştirilir. `FALSE`İyi performans sağlanmasına yardımcı olması için bu parametre için sıfır () geçişi yapmanızı öneririz. Önbelleğe almayı önlemek istiyorsanız, `DontCache` . vsct dosyasında komutu oluştururken bayrağını uygulayın. Bununla birlikte, bu bayrağı dikkatli bir şekilde kullanın veya performans azalabilir. Komut bayrakları hakkında daha fazla bilgi için bkz. [komut bayrağı öğe](../extensibility/command-flag-element.md) belgeleri.

    - Bir pencerede yerinde etkinleştirme modelini kullanarak bir ActiveX denetimi barındıran VSPackages içinde, yöntemi kullanmak daha uygun olabilir <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Arabirimindeki yöntemi ve <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> arabirimdeki yöntemi işlevsel olarak eşdeğerdir. Her ikisi de ortamın tüm komutların durumunu yeniden sorgulayamasına neden olur. Genellikle, bir güncelleştirme hemen gerçekleştirilmez. Bunun yerine, bir güncelleştirme, boşta kalma süresine kadar gecikir. Kabuk, iyi performans sağlanmasına yardımcı olması için komut durumunu önbelleğe alır. Önbelleğe almayı önlemek istiyorsanız, `DontCache` . vsct dosyasında komutu oluştururken bayrağını uygulayın. Yine de, performans azalabileceğinden, bu bayrağı dikkatle kullanın.

         <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> `QueryInterface` Bir nesne üzerinde yöntemini çağırarak <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> veya hizmetten arabirimi alarak arabirimi elde edebilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> .

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Uygulama](../extensibility/internals/command-implementation.md)
