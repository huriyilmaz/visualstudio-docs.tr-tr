---
title: Proje modelleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42e810a36478e49a578c6713d20f1bfc6be98309
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725567"
---
# <a name="project-modeling"></a>Proje Modelleme
Projeniz için Otomasyon sağlamaya yönelik bir sonraki adım, Standart proje nesnelerini uygulamaktır: <xref:EnvDTE.Projects> ve `ProjectItems` koleksiyonları; `Project` ve <xref:EnvDTE.ProjectItem> nesneleri; ve geri kalan nesneler uygulamanıza özeldir. Bu standart nesneler Dteınternal. h dosyasında tanımlanmıştır. BscPrj örneğinde standart nesneler için bir uygulama verilmiştir. Bu sınıfları, diğer proje türlerindeki proje nesneleriyle yan yana olan kendi standart proje nesnelerinizi oluşturmak için modeller olarak kullanabilirsiniz.

 Bir Otomasyon tüketicisi <xref:EnvDTE.Solution>("`<UniqueProjName>")` ve <xref:EnvDTE.ProjectItems> (`n`) çağırabilecektir. burada n, çözümde belirli bir projeyi almak için bir dizin numarasıdır. Bu Otomasyon çağrısını yapmak, ortamın uygun proje hiyerarşisinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> çağırmasını sağlar. Bu, VSITEMID_ROOT öğesini ItemId parametresi olarak ve VSHPROPID_ExtObject as VSHPROPID parametresi olarak. `IVsHierarchy::GetProperty`, Otomasyon nesnesine uygulamış olduğunuz çekirdek `Project` arabirimini sağlayan `IDispatch` bir işaretçi döndürür.

 `IVsHierarchy::GetProperty`sözdizimi aşağıda verilmiştir.

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT``*pvar`

 `);`

 Projeler, proje öğelerinin gruplarını oluşturmak için iç içe ve koleksiyonları kullanır. Hiyerarşi şuna benzer.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 İç içe geçme, bir `ProjectItems` koleksiyonu iç içe nesneleri içerebildiğinden, bir <xref:EnvDTE.ProjectItem> nesnenin aynı anda <xref:EnvDTE.ProjectItems> koleksiyon olabileceği anlamına gelir. Temel proje örneği bu iç içe geçme göstermez. `Project` nesnesini uygulayarak, genel otomasyon modelinin tasarımını gösteren ağaç benzeri yapıya katılırsanız.

 Proje Otomasyonu aşağıdaki diyagramdaki yolu izler.

 ![Visual Studio proje nesneleri](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Proje Otomasyonu

 `Project` nesnesi uygulamadıysanız, ortam hala yalnızca projenin adını içeren bir genel `Project` nesnesi döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>