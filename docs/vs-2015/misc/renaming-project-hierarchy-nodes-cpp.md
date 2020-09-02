---
title: Proje hiyerarşisi düğümlerini yeniden adlandırma (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- HierUtil7 sample [Visual Studio SDK], renaming project nodes
- project nodes, renaming in HierUtil7 sample
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: c7ad43fe1fd0e22cd94194d3079761de812b6ced
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686584"
---
# <a name="renaming-project-hierarchy-nodes-c"></a>Proje hiyerarşisi düğümlerini yeniden adlandırma (C++)
Yönetilmeyen C++ için HierUtil7 proje çerçevesini kullanarak proje klasörü hiyerarşisi düğümünü yeniden adlandırabilirsiniz. Daha fazla bilgi için bkz. [HierUtil7 Sample](https://msdn.microsoft.com/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## <a name="expanding-the-hierarchy-node"></a>Hiyerarşi düğümünü genişletme  
  
#### <a name="to-expand-the-hierarchy-node-and-rename-the-folder"></a>Hiyerarşi düğümünü genişletmek ve klasörü yeniden adlandırmak için  
  
1. Aşağıdaki yöntemi kullanarak hiyerarşi düğümünü seçin:  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` hiyerarşi kapsayıcısı klasöre karşılık gelir ve `EXPF_SelectItem` <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> numaralandırmadır. , `GUID_MacroExplorer` Vsshell. IDL ' de tanımlanan BIR GUID sabiti ve `rguidPersistenceSlot` `ExtExpand` Hu_node. h içinde tanımlanan, işlev imzasında için bir örnektir.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Hu_node. h dosyasını, \<installation root> \Program Files\vsıp 8.0 \ EnvSDK\common\hierutil7 klasöründe bulabilirsiniz:  
  
2. Yeniden adlandır komutunu kullanarak klasörü yeniden adlandırma <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> işaretçisidir: `<IVsUIShell>``srpVsUIShell` . `guiVSStd97` , `cmdidRename` Vsshlıds. h içinde tanımlanan komutun ait olduğu komut grubunun benzersiz tanımlayıcısıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje türleri oluşturma](../extensibility/internals/creating-project-types.md)   
 [VSSDK örnekleri](../misc/vssdk-samples.md)