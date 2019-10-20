---
title: İşlemleri kullanarak UML model güncelleştirmelerini bağlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, transactions
ms.assetid: a1df6c38-a3d1-4a3f-82bc-c8f363ab916e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8930bba76830a6116c3182f3fb2936cd4f1a3e47
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657602"
---
# <a name="link-uml-model-updates-by-using-transactions"></a>İşlemleri kullanarak UML model güncelleştirmelerini bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da UML tasarımcıları için bir uzantı tanımladığınızda, birden fazla değişikliği, *bağlantılı geri alma bağlamı*olarak adlandırılan tek bir işlem halinde gruplandırabilirsiniz. Hangi Visual Studio sürümlerini UML modellerini desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Varsayılan olarak, kodunuzun bir modele yaptığı her değişiklik Kullanıcı tarafından ayrı olarak geri alınabilir. Örneğin, iki UML sınıfının adlarını değiştiren bir menü komutu tanımlarsanız, bir kullanıcı komutu çağırabilir ve sonra tek bir geri alma işlemi gerçekleştirebilir. Bu, bir ada yapılan değişikliği geri alır, ancak başka bir durumda modelden istenmeyen bir durumda bırakır.

 Bunu önlemek için, kodunuz bir işlem içinde bir dizi değişiklik gerçekleştirebilir. Bu, değişikliklerin kullanıcıya tek bir değişiklik gibi görünmesine neden olur. Sonraki geri alma komutu serinin tamamını geri alacak.

 Ek bir avantaj, kodunuzun bir özel durum oluşturarak veya işlemi iptal ederek kısmen tamamlanmış bir değişiklik kümesini geri alabilir.

## <a name="to-group-changes-into-a-single-transaction"></a>Değişiklikleri tek bir işlemde gruplandırmak için
 Proje başvurularınızın bu .NET derlemesini içerdiğinden emin olun:

 **Microsoft. VisualStudio. model. SDK. [sürüm]. dll**

 Sınıfınız içinde, türü <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoContext> olan içeri aktarılmış bir özelliği bildirin:

 `using Microsoft.VisualStudio.Modeling.ExtensionEnablement;`

 `...`

 `class … {`

 `[Import]`

 `public ILinkedUndoContext LinkedUndoContext { get; set; }`

 Modeli değiştiren bir yöntemde, değişikliklerinizi bir işlem içine alın:

 `using (ILinkedUndoTransaction transaction =`

 `LinkedUndoContext.BeginTransaction("my updates"))`

 `{`

 `// code to update model elements or shapes goes here`

 `transaction.Commit();`

 `}`

 Aşağıdakilere dikkat edin:

- İşlemin sonuna `Commit()` her zaman dahil etmeniz gerekir. Bir işlem yürütülmeden atıldığı takdirde, işlem geri alınacaktır. Diğer bir deyişle, model işlemin başlangıcında durumuna geri yüklenecek.

- İşlem içinde yakalanamayan bir özel durum oluşursa, işlem geri alınacaktır. İşlemin `using` bloğunu `try…catch` bloğunun içine almak için sık kullanılan bir desendir.

- İşlemleri iç içe geçirebilirsiniz.

- @No__t_0 için boş olmayan bir ad sağlayabilirsiniz.

- Bu işlemlerden yalnızca UML model deposu etkilenir. Modelleme işlemleri etkilenmez: değişkenler, dosyalar ve veritabanları gibi dış depolar, katman diyagramları ve kod modelleri.

## <a name="example"></a>Örnek

```
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
    using Microsoft.VisualStudio.Uml.Interfaces;
    using Microsoft.VisualStudio.Uml.Classes;
    using Microsoft.VisualStudio.Uml.Extensions;
    using System.Linq;
    using System.ComponentModel.Composition;
 ...
  [Import]
  public ILinkedUndoContext LinkedUndoContext { get; set; }

  /// <summary>
  /// Swap the names of the currently selected elements.
  /// </summary>
  public void Execute(IMenuCommand command)
  {
    var selectedShapes =
      Context.CurrentDiagram.GetSelectedShapes<IClassifier>();
    if (selectedShapes.Count() < 2) return;
    IClassifier firstElement = selectedShapes.First().Element;
    IClassifier lastElement = selectedShapes.Last().Element;
    string firstName = firstElement.Name;
    // Perform changes inside a transaction so that undo
    // works as a single change.
    using (ILinkedUndoTransaction transaction =
      LinkedUndoContext.BeginTransaction("Swap names"))
    {
        firstElement.Name = lastElement.Name;
        lastElement.Name = firstName;
        transaction.Commit();
    }
 }
```

## <a name="see-also"></a>Ayrıca Bkz.
 [UML API Ile programlama](../modeling/programming-with-the-uml-api.md) [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [UML modellerini ve Diyagramları Genişletme](../modeling/extend-uml-models-and-diagrams.md)
