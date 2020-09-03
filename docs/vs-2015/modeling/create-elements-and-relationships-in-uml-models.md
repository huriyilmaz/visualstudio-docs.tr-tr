---
title: UML modellerinde öğe ve ilişki oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: cae81d32-8cc7-4f7c-9f00-20119952bc51
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5ea066aa31cbc1f6408ee55c92a5ca761608f534
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667822"
---
# <a name="create-elements-and-relationships-in-uml-models"></a>UML modellerinde öğe ve ilişki oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio uzantısı için program kodunda, öğe ve ilişki oluşturabilir ve silebilirsiniz.

## <a name="create-a-model-element"></a>Model öğesi oluşturma

### <a name="namespace-imports"></a>Ad alanı Içeri aktarmaları
 Aşağıdaki deyimleri dahil etmeniz gerekir `using` .

 Oluşturma yöntemleri, bu ad alanında uzantı yöntemleri olarak tanımlanmıştır:

 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`

### <a name="obtain-the-owner-of-the-element-you-want-to-create"></a>Oluşturmak istediğiniz öğenin sahibini edinin
 Model, her öğenin model kökü dışında bir sahibe sahip olması için tek bir ağaç oluşturur. Model kökü, türü olan türüdür `IModel` `IPackage` .

 Belirli bir diyagramda görüntülenecek bir öğe oluşturuyorsanız (örneğin, kullanıcının geçerli diyagramı), genellikle onu bu diyagrama bağlı pakette oluşturmanız gerekir. Örneğin:

```
IPackage linkedPackage = Context.CurrentDiagram.Element as IPackage;
```

 Bu tablo ortak model öğelerinin sahipliğini özetler:

|Oluşturulacak öğe|Sahip|
|---------------------------|-----------|
|`IActor, IUseCase, IComponent, IClass, IInterface, IEnumeration`<br /><br /> `IActivity, IInteraction`|`IPackage, IModel`|
|`IAttribute, IOperation`|`IClass, IInterface`|
|`IPart, IPort`|`IComponent`|
|`IAction, IObjectNode`|`IActivity`|
|`ILifeline, IMessage, ICombinedFragment`|`IInteraction`|

### <a name="invoke-the-create-method-on-the-owner"></a>Sahibe oluşturma yöntemini çağır
 Yöntem adı şu biçimdedir: `Create` *ownedtype* `()` . Örneğin:

```
IUseCase usecase1 = linkedPackage.CreateUseCase();
```

 Bazı türlerin özellikle sıralı diyagramlarda daha karmaşık oluşturma yöntemleri vardır. Bkz. [UML API kullanarak UML sıra diyagramlarını düzenleme](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

 Bazı öğe türleri için, kullanarak bir öğenin sahibini ömrü boyunca değiştirebilirsiniz `SetOwner(newOwner)` .

### <a name="set-the-name-and-other-properties"></a>Adı ve diğer özellikleri ayarlama

```
usecase1.Name = "user logs in";
```

### <a name="example"></a>Örnek

```
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.Uml.Extensions;
...
 void InstantiateObserverPattern (IPackage package, string namePrefix)
 {    IInterface observer = package.CreateInterface();
      observer.Name = namePrefix + "Observer";
      IOperation operation = observer.CreateOperation();
      operation.Name = "Update";
      IClass subject = package.CreateClass();
      subject.Name = namePrefix + "Subject"; ...
```

## <a name="create-an-association"></a>Ilişki oluşturma

#### <a name="to-create-an-association"></a>Bir ilişki oluşturmak için

1. İlişkinin sahibini alma, genellikle ilişkinin kaynak sonunu içeren paket veya model.

2. Sahip üzerinde gerekli oluşturma yöntemini çağırın.

3. İlişkinin adı gibi özelliklerini ayarlayın.

     Örneğin:

    ```
    IAssociation association = subject.Package.CreateAssociation(subject, observer);
    association .Name = "Observes";
    ```

4. İlişkinin her ucunun özelliklerini ayarlayın. Her zaman iki vardır `MemberEnds` . Örneğin:

    ```
    association .MemberEnds[0].Name = "subject";   // role name
    association .MemberEnds[1].Name = "observers"; // role name
    association .MemberEnds[1].SetBounds("0..*");
                // multiplicity defaults to "1"
    association.MemberEnds[0].Aggregation = AggregationKind.Composite;
    ```

## <a name="create-a-generalization"></a>Genelleştirme oluşturma

```
IGeneralization generalization =
  subclass.CreateGeneralization(superClass);
```

## <a name="delete-an-element-relationship-or-generalization-from-the-model"></a>Modelden bir öğe, Ilişki veya genelleştirme silme

```
anElement.Delete();
```

 Bir modelden bir öğe sildiğinizde:

- Onunla bağlantılı her ilişki de silinir.

- Diyagramda temsil eden her şekil de silinir.

## <a name="see-also"></a>Ayrıca Bkz.
 [UML modellerini ve Diyagramları Genişletme](../modeling/extend-uml-models-and-diagrams.md) [diyagramlarda bir UML modeli görüntüleme](../modeling/display-a-uml-model-on-diagrams.md)
