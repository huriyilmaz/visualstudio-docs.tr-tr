---
title: Kullanıcı Arabiriminin Güncellenmesi | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698884"
---
# <a name="updating-the-user-interface"></a>Kullanıcı Arabirimini Güncelleştirme
Bir komut uyguladıktan sonra, kullanıcı arabirimini yeni komutlarınızın durumuyla güncelleştirmek için kod ekleyebilirsiniz.

 Tipik bir Win32 uygulamasında, komut kümesi sürekli olarak yoklanabilir ve tek tek komutların durumu kullanıcı bunları görüntüledikçe ayarlanabilir. Ancak, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kabuk sınırsız sayıda VSPackages barındırabildiği için, kapsamlı yoklama yanıt verme yeteneğini azaltabilir, özellikle yönetilen kod ve COM arasındaki interop derlemeleri arasında yoklama.

### <a name="to-update-the-ui"></a>Kullanıcı Bira'sını güncelleştirmek için

1. Aşağıdaki adımlardan birini uygulayın:

    - <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> Yöntemi ara.

         Aşağıdaki gibi hizmetten bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> arayüz elde edilebilir. <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

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

         Parametresi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> sıfır değilse (),`TRUE`güncelleştirme eşzamanlı olarak ve hemen gerçekleştirilir. İyi performansı korumaya yardımcı`FALSE`olmak için bu parametre için sıfırı geçmenizi öneririz. Önbelleğe alma maksatını `DontCache` önlemek istiyorsanız, .vsct dosyasındaki komutu oluştururken bayrağı uygulayın. Yine de, bayrağı dikkatli kullanın veya performans düşebilir. Komut bayrakları hakkında daha fazla bilgi için [Komut Bayrağı Öğesi](../extensibility/command-flag-element.md) belgelerine bakın.

    - Bir penceredeki yerinde etkinleştirme modelini kullanarak ActiveX denetimini barındıran <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> VSPackages'ta, yöntemi kullanmak daha uygun olabilir. Arabirimdeki <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> yöntem ve <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> arabirimdeki yöntem işlevsel olarak eşdeğerdir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Her ikisi de ortamın tüm komutların durumunu yeniden sorgulamasına neden olur. Genellikle, bir güncelleştirme hemen gerçekleştirilmez. Bunun yerine, bir güncelleştirme boşta kalma süresine kadar geciktirilir. Kabuk, iyi performansı korumaya yardımcı olmak için komut durumunu önbelleğe alıyor. Önbelleğe alma maksatını `DontCache` önlemek istiyorsanız, .vsct dosyasındaki komutu oluştururken bayrağı uygulayın. Yine de, performans düşebileceğinden bayrağı dikkatli kullanın.

         Bir <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> nesne üzerinde <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> `QueryInterface` yöntemi arayarak veya hizmetten arabirimi alarak arabirimi elde edebilirsiniz dikkat edin.

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Uygulama](../extensibility/internals/command-implementation.md)
