---
title: Project Modelleme | Microsoft Docs
description: Yeni proje türünüz için otomasyon oluşturmak için gereken standart proje nesneleri ve proje otomasyonu yolunu öğrenin.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7edc9fe6e4703315356d5289f0054d2aacdbe76c9e752c4b8608e8e58f32e38e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359226"
---
# <a name="project-modeling"></a>Proje Modelleme
Projeniz için otomasyon sağlamanın bir sonraki adımı standart proje nesnelerini <xref:EnvDTE.Projects> uygulamaktır: ve koleksiyonları; ve nesneleri ve uygulamanıza özgü `ProjectItems` `Project` kalan <xref:EnvDTE.ProjectItem> nesneler. Bu standart nesneler Dteinternal.h dosyasında tanımlanır. Standart nesnelerin uygulaması BscPrj örneğinde sağlanır. Bu sınıfları model olarak kullanarak diğer proje türlerinden proje nesneleriyle yan yana olan kendi standart proje nesnelerinizi oluşturabilirsiniz.

 Otomasyon tüketicisi, n'nin çözümde belirli bir projeyi almak için dizin numarası olduğu (" ve ( ) çağrısına sahip <xref:EnvDTE.Solution> `<UniqueProjName>")` olduğunu <xref:EnvDTE.ProjectItems> `n` varsayıyor. Bu otomasyon çağrısını yapmak, ortamın uygun proje hiyerarşisinde çağrısı yaparak VSITEMID_ROOT ItemID parametresi olarak geçirmesine ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> VSHPROPID_ExtObject VSHPROPID parametresi olarak çalışmasına neden olur. `IVsHierarchy::GetProperty` , `IDispatch` benimsersiniz çekirdek arabirimini `Project` sağlayan otomasyon nesnesine bir işaretçi döndürür.

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

 İç içe yerleştirme, bir nesnenin aynı anda toplanmış olması anlamına <xref:EnvDTE.ProjectItem> gelir çünkü bir koleksiyon iç içe geçmiş nesneleri <xref:EnvDTE.ProjectItems> `ProjectItems` içerebilir. Temel Project örneği bu iç içe yerleştirmeyi göstermez. nesnesini uygulayarak, genel otomasyon modelinin tasarımını ifade etmek için ağaç `Project` gibi bir yapıya katılabilirsiniz.

 Proje otomasyonu aşağıdaki diyagramda yer alan yolu izler.

 ![Visual Studio Project Nesneleri Project](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") otomasyonu

 Bir nesnesi uygulamazsanız, ortam yine de yalnızca projenin adını `Project` içeren genel bir nesne geri `Project` döner.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
