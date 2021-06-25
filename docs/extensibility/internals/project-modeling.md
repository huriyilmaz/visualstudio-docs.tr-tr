---
title: Proje Modelleme | Microsoft Docs
description: Yeni proje türünüz için otomasyon oluşturmak için gereken standart proje nesneleri ve proje otomasyonu tarafından takip eden yol hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b90271fcc43c627f2eb7dbb2f318427ad0d9839e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899686"
---
# <a name="project-modeling"></a>Proje Modelleme
Projeniz için otomasyon sağlamanın bir sonraki adımı, standart proje nesnelerini <xref:EnvDTE.Projects> uygulamaktır: ve koleksiyonları; ve nesneleri ve uygulamanıza özgü `ProjectItems` `Project` kalan <xref:EnvDTE.ProjectItem> nesneler. Bu standart nesneler Dteinternal.h dosyasında tanımlanır. Standart nesnelerin uygulaması BscPrj örneğinde sağlanır. Bu sınıfları model olarak kullanarak diğer proje türlerinden proje nesneleriyle yan yana olan kendi standart proje nesnelerinizi oluşturabilirsiniz.

 Otomasyon tüketicisi, n'nin çözümde belirli bir projeyi almak için dizin numarası olduğu (" ve ( ) çağrısına sahip <xref:EnvDTE.Solution> `<UniqueProjName>")` olduğunu <xref:EnvDTE.ProjectItems> `n` varsayıyor. Bu otomasyon çağrısını yapmak, ortamın uygun proje hiyerarşisinde çağrısı yaparak VSITEMID_ROOT ItemID parametresi olarak geçirmesine ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> bunu VSHPROPID parametresi VSHPROPID_ExtObject olarak geçirmesine neden olur. `IVsHierarchy::GetProperty` , `IDispatch` uygulaymış olduğu çekirdek arabirimini sağlayan `Project` otomasyon nesnesine bir işaretçi döndürür.

 Aşağıdaki `IVsHierarchy::GetProperty` sözdizimidir.

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Projeler iç içe yerleştirmeye uyum sağlar ve proje öğeleri grupları oluşturmak için koleksiyonları kullanır. Hiyerarşi aşağıdaki gibi görünür.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 İç içe yerleştirme, bir nesnenin aynı anda toplanmış olması anlamına <xref:EnvDTE.ProjectItem> gelir çünkü bir koleksiyon iç içe geçmiş nesneleri <xref:EnvDTE.ProjectItems> `ProjectItems` içerebilir. Temel Proje örneği bu iç içe yerleştirmeyi göstermez. nesnesini uygulayarak, genel otomasyon modelinin tasarımını ifade etmek için ağaç `Project` gibi bir yapıya katılabilirsiniz.

 Proje otomasyonu aşağıdaki diyagramda yer alan yolu izler.

 ![Visual Studio Nesnelerini Oluşturma](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Proje otomasyonu

 Bir nesnesi uygulamazsanız, ortam yine de yalnızca projenin adını `Project` içeren genel bir nesne geri `Project` döner.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
