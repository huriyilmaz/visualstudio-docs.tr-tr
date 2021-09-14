---
title: Otomasyon Modeli | Microsoft Docs
description: VSPackage'nizin otomasyon modeline bağlandıktan sonra özelliklerini ve yöntemlerini nasıl elde etmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d57979e3913f9bfbfd4b782574de012b3f8523bf
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627297"
---
# <a name="using-the-automation-model"></a>Otomasyon Modelini Kullanma
VSPackage'nızı otomasyona bağladıktan sonra nesnesinde yöntemini çağırarak, almak istediğiniz nesneyi temsil eden bir dizeyi geçerek özellikleri <xref:EnvDTE.DTEClass.GetObject%2A> <xref:EnvDTE._DTE> ve yöntemleri elde edersiniz.

## <a name="obtaining-project-objects"></a>Project Alma
 Aşağıda, otomasyon tüketicisi tarafından proje otomasyonu nesnelerini nasıl edinilene yönelik iki kod örneği verilmiştir. DTE nesnesinin nasıl elde edildiklerine ilişkin bilgi için bkz. Nasıl [kullanılır: DTE ve DTE2 Nesnelerine BaşvuruLar Al.](/previous-versions/68shb4dw(v=vs.140))

```vb
Sub DoAutomation()
    Dim MyProjects As Projects
    MyProjects = DTE.GetObject("AcmeProject")
End Sub
```

```cpp
void DoAutomation(void)
{
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.
    pMyPkg = pDTE->GetObject("AcmeProjects");

   // The '=' performs a Query Interface.
   // Assumes pDTE is already available as a global.
   // Use pMyPkg to access your projects object's properties and methods.
}

```

 Bu noktada, hiyerarşi modelini aşağı taşımak için belirli bir VSPackage'ın parçası olan standart proje nesnelerini kullanabilirsiniz.

 Aşağıdaki kod örneği, özel bir proje türünün özelliği olan özel bir nesnenin nasıl elde etmek üzere olduğunu gösterir:

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 Aşağıdaki kod, Araçlar menüsündeki Ortam Genel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] seçeneğinde bulunan **tüm** özelliklerin **adlarını** listeler:

```vb
dim objDTE
dim objEnv
set objDTE = CreateObject("VisualStudio.DTE")
set objEnv = objDTE.Properties("Environment", "General")
for each obj in ObjEnv
MsgBox obj.Name
Next

```

## <a name="see-also"></a>Ayrıca bkz.
- <xref:EnvDTE.DTEClass.GetObject%2A>