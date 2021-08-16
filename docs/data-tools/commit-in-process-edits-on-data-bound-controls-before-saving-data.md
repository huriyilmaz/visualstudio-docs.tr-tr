---
title: Kaydedilmemiş düzenlemeler
description: veri kaydedilmeden önce veriye bağlı Windows Forms denetimlerinde işlem içi düzenlemeleri yürütün. Form üzerindeki tüm BindingSource bileşenleri için EndEdit 'u çağırın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1cee28208d40de90039306acff40ffdd650cd236aa6935e473e8389efa232302
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347811"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Verileri kaydetmeden önce verilere bağlı denetimler üzerinde işlem içi düzenlemeler yürütme

Veri bağlantılı denetimlerde değerler düzenlenirken, kullanıcılar, güncelleştirilmiş değeri denetimin bağlandığı temel alınan veri kaynağına uygulamak için geçerli kaydın üzerinde gezinmelidir. Öğeleri [veri kaynakları penceresinden](add-new-data-sources.md) bir form üzerine sürüklediğinizde, sürüklediğiniz ilk öğe, **Kaydet** düğmesine tıklama olayına kodu oluşturur <xref:System.Windows.Forms.BindingNavigator> . Bu kod <xref:System.Windows.Forms.BindingSource.EndEdit%2A> , yöntemini çağırır <xref:System.Windows.Forms.BindingSource> . Bu nedenle, yöntemine yapılan çağrı <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yalnızca forma eklenen ilk için oluşturulur <xref:System.Windows.Forms.BindingSource> .

<xref:System.Windows.Forms.BindingSource.EndEdit%2A>Çağrı, şu anda düzenlenmekte olan herhangi bir veri bağlantılı denetimlerde, işlemdeki tüm değişiklikleri kaydeder. Bu nedenle, bir veri bağlantılı denetim hala odağa sahipse ve **Kaydet** düğmesine tıklarsanız, o denetimdeki tüm bekleyen düzenlemeler gerçek kaydetme işleminden ( `TableAdapterManager.UpdateAll` yöntemi) önce işlenir.

Bir Kullanıcı, değişiklikleri kaydetmeden, kaydetme işleminin bir parçası olarak verileri kaydetmeye çalışırsa bile, uygulamanızı otomatik olarak değişiklikleri işleyecek şekilde yapılandırabilirsiniz.

> [!NOTE]
> Tasarımcı `BindingSource.EndEdit` kodu yalnızca bir form üzerine bırakılan ilk öğe için ekler. Bu nedenle, <xref:System.Windows.Forms.BindingSource.EndEdit%2A> form üzerinde her biri için yöntemini çağırmak üzere bir kod satırı eklemeniz gerekir <xref:System.Windows.Forms.BindingSource> . Her biri için yöntemi çağırmak üzere bir kod satırı el ile ekleyebilirsiniz <xref:System.Windows.Forms.BindingSource.EndEdit%2A> <xref:System.Windows.Forms.BindingSource> . Alternatif olarak, `EndEditOnAllBindingSources` Bu yöntemi forma ekleyebilirsiniz ve Kaydet işlemini gerçekleştirmeden önce çağırabilirsiniz.

Aşağıdaki kod, bir [LINQ (dil Ile tümleşik sorgu)](/dotnet/csharp/linq/) sorgusunu kullanarak tüm bileşenleri yineleyebilir <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingSource.EndEdit%2A> her bir form için yöntemini çağırır <xref:System.Windows.Forms.BindingSource> .

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Form üzerindeki tüm BindingSource bileşenleri için EndEdit 'u çağırmak için

1. Bileşenleri içeren forma aşağıdaki kodu ekleyin <xref:System.Windows.Forms.BindingSource> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet1":::

2. Form verilerini kaydetmek için herhangi bir çağrının hemen öncesine aşağıdaki kod satırını ekleyin ( `TableAdapterManager.UpdateAll()` yöntemi):

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet2":::

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)
