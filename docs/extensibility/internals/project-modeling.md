---
title: Proje modelleme | Microsoft Docs
description: Yeni proje türü için Otomasyon oluşturmak için gereken standart proje nesneleri ve Proje Otomasyonu 'nun aşağıdaki yolu hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 7a481e731f01230139ec4342231479606c49bd11
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877422"
---
# <a name="project-modeling"></a>Proje Modelleme
Projeniz için Otomasyon sağlamanın bir sonraki adımı, Standart proje nesneleri: <xref:EnvDTE.Projects> ve koleksiyonları; ve `ProjectItems` `Project` <xref:EnvDTE.ProjectItem> nesneleri ve geri kalan nesneleri uygulamanıza özel olarak uygulamaktır. Bu standart nesneler Dteınternal. h dosyasında tanımlanmıştır. BscPrj örneğinde standart nesneler için bir uygulama verilmiştir. Bu sınıfları, diğer proje türlerindeki proje nesneleriyle yan yana olan kendi standart proje nesnelerinizi oluşturmak için modeller olarak kullanabilirsiniz.

 Bir Otomasyon tüketicisi, <xref:EnvDTE.Solution> (" `<UniqueProjName>")` ve <xref:EnvDTE.ProjectItems> ( `n` ). burada n, çözümde belirli bir projeyi almak için bir dizin numarası olarak çağrı yapabilecektir. Bu Otomasyon çağrısını yapmak <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> , ortamın uygun proje hiyerarşisinde çağrı yapmasına, VSITEMID_ROOT ItemId parametresi olarak VSHPROPID_ExtObject ve VSHPROPID parametresi olarak. `IVsHierarchy::GetProperty``IDispatch`uygulamış olduğunuz çekirdek arabirimini sağlayan Automation nesnesine bir işaretçi döndürür `Project` .

 Aşağıdaki sözdizimi aşağıda verilmiştir `IVsHierarchy::GetProperty` .

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Projeler, proje öğelerinin gruplarını oluşturmak için iç içe ve koleksiyonları kullanır. Hiyerarşi şuna benzer.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 İç içe geçme, bir <xref:EnvDTE.ProjectItem> <xref:EnvDTE.ProjectItems> `ProjectItems` koleksiyonun iç içe geçmiş nesneleri içerebildiğinden, bir nesnenin aynı anda koleksiyon olabileceği anlamına gelir. Temel proje örneği bu iç içe geçme göstermez. `Project`Nesnesini uygulayarak, genel otomasyon modelinin tasarımını gösteren ağaç benzeri yapıya katılırsanız.

 Proje Otomasyonu aşağıdaki diyagramdaki yolu izler.

 ![Visual Studio proje nesneleri](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Proje Otomasyonu

 Bir nesne gerçekleştirmeyin `Project` , ortam hala `Project` yalnızca projenin adını içeren genel bir nesne döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
