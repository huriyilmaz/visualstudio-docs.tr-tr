---
title: Otomasyon modelini kullanma | Microsoft Docs
description: VSPackage 'ın Otomasyon modeline bağlandıktan sonra özellik ve yöntemlerini nasıl edineceğinizi öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086449"
---
# <a name="using-the-automation-model"></a>Otomasyon Modelini Kullanma
VSPackage 'ı Otomasyon 'a bağladıktan sonra, <xref:EnvDTE.DTEClass.GetObject%2A> nesne üzerinde yöntemini çağırarak ve <xref:EnvDTE._DTE> almak istediğiniz nesneyi temsil eden bir dize geçirerek özellikleri ve yöntemleri elde edebilirsiniz.

## <a name="obtaining-project-objects"></a>Project nesneleri alma
 Aşağıda, bir Otomasyon tüketicisinin Proje Otomasyonu nesnelerini nasıl aldığını gösteren iki kod örneği verilmiştir. DTE nesnesini alma hakkında daha fazla bilgi için bkz. [nasıl yapılır: DTE ve DTE2 nesnelerine başvuruları alma](/previous-versions/68shb4dw(v=vs.140)).

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

 Bu noktada, belirli bir VSPackage 'ın parçası olan standart proje nesnelerini hiyerarşi modelinin altına taşımak için kullanabilirsiniz.

 Aşağıdaki kod örneği, özel bir proje türünün özelliği olan özel bir nesnenin nasıl alınacağını gösterir.:

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 Aşağıdaki kod, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Araçlar** menüsündeki ortam **genel** seçeneğinde tüm özelliklerin adlarını listeler:

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