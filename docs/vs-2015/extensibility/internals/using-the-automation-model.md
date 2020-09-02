---
title: Otomasyon modelini kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22ee836f5a4330c551181f01229e82eb14623fb8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675205"
---
# <a name="using-the-automation-model"></a>Otomasyon Modelini Kullanma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage 'ı Otomasyon 'a bağladıktan sonra, <xref:EnvDTE.DTEClass.GetObject%2A> nesne üzerinde yöntemini çağırarak ve <xref:EnvDTE._DTE> almak istediğiniz nesneyi temsil eden bir dize geçirerek özellikleri ve yöntemleri elde edebilirsiniz.  
  
## <a name="obtaining-project-objects"></a>Proje nesneleri alma  
 Aşağıda, bir Otomasyon tüketicisinin Proje Otomasyonu nesnelerini nasıl aldığını gösteren iki kod örneği verilmiştir. DTE nesnesini alma hakkında daha fazla bilgi için bkz. [nasıl yapılır: DTE ve DTE2 nesnelerine başvuruları alma](https://msdn.microsoft.com/library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).  
  
```vb  
Sub DoAutomation()  
    Dim MyProjects As Projects  
    MyProjects = DTE.GetObject("AcmeProject")  
End Sub  
```  
  
```cpp#  
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
  
 Aşağıdaki kod, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Araçlar** menüsündeki ortam **genel** seçeneğinde tüm özelliklerin adlarını listeler:  
  
```vb  
dim objDTE  
dim objEnv  
set objDTE = CreateObject("VisualStudio.DTE")  
set objEnv = objDTE.Properties("Environment", "General")  
for each obj in ObjEnv  
MsgBox obj.Name  
Next  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:EnvDTE.DTEClass.GetObject%2A>
