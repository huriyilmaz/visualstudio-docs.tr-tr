---
title: Iç Içe projeler için komut Işlemeyi uygulama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2fbce80b2e8c337eddf0d34954a7fd70b895d891
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64804832"
---
# <a name="implementing-command-handling-for-nested-projects"></a>İç içe Projeler için Komut İşlemesi Uygulama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimleri aracılığıyla iç içe projelere geçirilen komutları geçirebilir veya üst projeler komutları filtreleyebilir veya geçersiz kılabilir.  
  
> [!NOTE]
> Yalnızca üst proje tarafından normalde işlenen komutlar filtrelenebilir. IDE tarafından işlenen **derleme** ve **dağıtım** gibi komutlar filtrelenemez.  
  
 Aşağıdaki adımlarda komut işlemeyi uygulama işlemi açıklanır.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-implement-command-handling"></a>Komut işlemeyi uygulamak için  
  
1. Kullanıcı iç içe geçmiş bir proje veya iç içe geçmiş bir projede bir düğüm seçtiğinde:  
  
   1. IDE <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntemini çağırır.  
  
      veya  
  
   2. Komut, Çözüm Gezgini içindeki kısayol menü komutu gibi bir hiyerarşi penceresinde başlatıldıysa IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> projenin üst kısmında yöntemini çağırır.  
  
2. Üst proje, `QueryStatus` `pguidCmdGroup` `prgCmds` ana projenin komutları filtreleyip filtreleyeceğini anlamak için, ve gibi geçirilecek parametreleri inceleyebilir. Üst proje, filtre komutlarına uygulanmışsa, şu şekilde ayarlanmalıdır:  
  
   ```  
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
   // make sure it is disabled  
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
   ```  
  
    Sonra üst proje döndürmelidir `S_OK` .  
  
    Üst proje komutu filtrelemez, yalnızca döndürmelidir `S_OK` . Bu durumda IDE, komutu otomatik olarak alt projeye yönlendirir.  
  
    Üst projenin komutu alt projeye yönlendirmesi gerekmez. IDE bu görevi gerçekleştirir...  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Komutlar, menüler ve araç çubukları](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [Projeleri İç İçe Geçirme](../../extensibility/internals/nesting-projects.md)
