---
title: Proje Modelleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1ac89baf5bc7582d3430532938a5e5a0c35a4c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706548"
---
# <a name="project-modeling"></a>Proje Modelleme
Projeniz için otomasyon sağlamanın bir sonraki adımı standart proje <xref:EnvDTE.Projects> nesnelerini uygulamaktır: ve `ProjectItems` koleksiyonlar; `Project` ve <xref:EnvDTE.ProjectItem> nesneler; ve uygulamanıza özgü kalan nesneler. Bu standart nesneler Dteinternal.h dosyasında tanımlanır. Standart nesnelerin uygulanması BscPrj örneğinde sağlanır. Bu sınıfları, diğer proje türlerinden gelen proje nesneleriyle yan yana duran kendi standart proje nesnelerinizi oluşturmak için model olarak kullanabilirsiniz.

 Bir otomasyon tüketicisi, çözümde`<UniqueProjName>")` belirli <xref:EnvDTE.ProjectItems> `n`bir proje elde etmek için n'nin bir dizin numarası olduğu yerde (" ve ( ) arama <xref:EnvDTE.Solution>yapabilmeyi varsar. Bu otomasyon çağrısının yapılması, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> ortamın uygun proje hiyerarşisini aramasına, VSITEMID_ROOT ItemID parametresi olarak geçmesine ve VSHPROPID parametresi olarak VSHPROPID_ExtObject neden olur. `IVsHierarchy::GetProperty`uyguladığınız `IDispatch` çekirdek `Project` arabirimi sağlayan otomasyon nesnesine bir işaretçi döndürür.

 Aşağıdaki sözdizimi `IVsHierarchy::GetProperty`.

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Projeler iç içe geçme yi barındırır ve proje öğeleri grupları oluşturmak için koleksiyonları kullanır. Hiyerarşi şuna benziyor.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 İç içe geçme, <xref:EnvDTE.ProjectItem> bir <xref:EnvDTE.ProjectItems> `ProjectItems` koleksiyonun iç içe geçen nesneleri içerebileceğinden, nesnenin aynı anda toplanabileceği anlamına gelir. Temel Proje örneği bu iç içe geçmeyi göstermez. Nesneyi `Project` uygulayarak, genel otomasyon modelinin tasarımını karakterize eden ağaç benzeri yapıya katılırsınız.

 Proje otomasyonu aşağıdaki diyagramdaki yolu izler.

 ![Visual Studio Proje Nesneleri](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Proje otomasyonu

 Bir `Project` nesne uygulamazsanız, ortam yine de `Project` yalnızca projenin adını içeren genel bir nesne döndürecektir.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
