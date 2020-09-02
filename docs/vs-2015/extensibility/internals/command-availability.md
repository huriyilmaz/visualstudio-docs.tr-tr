---
title: Komut kullanılabilirliği | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f060f6c49fc02c75b3fe9f792133c9ee88c6d56c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64780981"
---
# <a name="command-availability"></a>Komut Kullanılabilirliği
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio bağlamı hangi komutların kullanılabilir olduğunu belirler. Bağlam geçerli projeye, geçerli düzenleyiciye, yüklenen VSPackages ve tümleşik geliştirme ortamının (IDE) diğer yönlerini bağlı olarak değişebilir.  
  
## <a name="command-contexts"></a>Komut bağlamları  
 Aşağıdaki komut bağlamları en yaygın bir deyişle.  
  
- **IDE** IDE tarafından sağlanan komutlar her zaman kullanılabilir.  
  
- **VSPackage** VSPackages, komutların ne zaman gösterileceğini veya gizlendiğini tanımlayabilir.  
  
- **Proje** Proje komutları yalnızca şu anda seçili proje için görünür.  
  
- **Düzenleyici** Tek seferde yalnızca bir düzenleyici etkin olabilir. Etkin düzenleyiciden komutlar var. Bir düzenleyici, dil hizmetiyle yakından birlikte çalışmaktadır. Dil hizmeti, komutlarını ilişkili düzenleyicinin bağlamında işlemelidir.  
  
- **Dosya türü** Bir düzenleyici, birden fazla dosya türü yükleyebilir. Kullanılabilir komutlar dosya türüne bağlı olarak değişebilir.  
  
- **Etkin pencere** Son etkin belge penceresi, anahtar bağlamaları için Kullanıcı arabirimi (UI) bağlamını ayarlar. Ancak, iç Web tarayıcısına benzer bir anahtar bağlama tablosuna sahip bir araç penceresi de UI bağlamını ayarlayabilir. HTML Düzenleyicisi gibi çok sekmeli belge pencereleri için her sekmenin farklı bir komut bağlamı GUID 'i vardır. Bir araç penceresi kaydedildikten sonra, **Görünüm** menüsünde her zaman kullanılabilir.  
  
- **UI bağlamı** UI bağlamları, sınıf değerleri tarafından tanımlanır <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> , örneğin, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> çözüm derlenmekte veya <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> hata ayıklayıcısı etkin olduğunda. Aynı anda birden çok UI bağlamı etkin olabilir.  
  
## <a name="defining-custom-context-guids"></a>Özel bağlam GUID 'Leri tanımlama  
 Uygun bir komut bağlamı GUID 'SI zaten tanımlanmamışsa, VSPackage içinde bir tane tanımlayabilir ve ardından komutlarınızın görünürlüğünü denetlemek için gerektiğinde etkin veya devre dışı olarak programlayabilirsiniz.  
  
1. Metodu çağırarak bağlam GUID 'Lerini kaydettirin <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> .  
  
2. Yöntemini çağırarak bağlam GUID 'inin durumunu alın <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> .  
  
3. Yöntemini çağırarak bağlam GUID 'Lerini açın ve kapatın <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> .  
  
    > [!CAUTION]
    > Diğer VSPackages bunlara bağlı olabileceğinden VSPackage 'ın var olan herhangi bir bağlam GUID 'i etkilemediğinden emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Seçim bağlamı nesneleri](../../extensibility/internals/selection-context-objects.md)   
 [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
