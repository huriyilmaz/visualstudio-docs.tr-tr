---
title: Kaydetmeden önce veri bağlantılı denetimlerde işlem içi düzenlemeleri işleme
ms.date: 11/04/2016
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 129f8e03ca982dc1e028dc23a9e342b5793e39cf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648684"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Verileri kaydetmeden önce verilere bağlı denetimler üzerinde işlem içi düzenlemeler yürütme

Veri bağlantılı denetimlerde değerler düzenlenirken, kullanıcılar, güncelleştirilmiş değeri denetimin bağlandığı temel alınan veri kaynağına uygulamak için geçerli kaydın üzerinde gezinmelidir. Öğeleri [veri kaynakları penceresinden](add-new-data-sources.md) bir form üzerine sürüklediğinizde, sürüklediğiniz ilk öğe <xref:System.Windows.Forms.BindingNavigator> **Kaydet** düğmesi tıklama olayına kodu oluşturur. Bu kod, <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemini çağırır. Bu nedenle, <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemine yapılan çağrı yalnızca forma eklenen ilk <xref:System.Windows.Forms.BindingSource> için oluşturulur.

@No__t_0 çağrısı, şu anda düzenlenmekte olan herhangi bir veri bağlantılı denetimlerde, işlemdeki tüm değişiklikleri kaydeder. Bu nedenle, veri bağlantılı bir denetim hala odağa sahipse ve **Kaydet** düğmesine tıklarsanız, bu denetimdeki tüm bekleyen düzenlemeler gerçek kaydetme işleminden önce (`TableAdapterManager.UpdateAll` yöntemi) kaydedilir.

Bir Kullanıcı, değişiklikleri kaydetmeden, kaydetme işleminin bir parçası olarak verileri kaydetmeye çalışırsa bile, uygulamanızı otomatik olarak değişiklikleri işleyecek şekilde yapılandırabilirsiniz.

> [!NOTE]
> Tasarımcı, yalnızca bir forma bırakılan ilk öğe için `BindingSource.EndEdit` kodunu ekler. Bu nedenle, formdaki her bir <xref:System.Windows.Forms.BindingSource> için <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemini çağırmak üzere bir kod satırı eklemeniz gerekir. Her <xref:System.Windows.Forms.BindingSource> için <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemini çağırmak üzere bir kod satırı el ile ekleyebilirsiniz. Alternatif olarak, `EndEditOnAllBindingSources` yöntemini forma ekleyebilir ve kaydetme işlemini gerçekleştirmeden önce bu yöntemi çağırabilirsiniz.

Aşağıdaki kod, tüm <xref:System.Windows.Forms.BindingSource> bileşenlerini yinelemek ve bir formdaki her <xref:System.Windows.Forms.BindingSource> için <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemini çağırmak üzere bir [LINQ (dil Ile tümleşik sorgu)](/dotnet/csharp/linq/) sorgusu kullanır.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Form üzerindeki tüm BindingSource bileşenleri için EndEdit 'u çağırmak için

1. Aşağıdaki kodu <xref:System.Windows.Forms.BindingSource> bileşenleri içeren forma ekleyin.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2. Form verilerini kaydetmek için herhangi bir çağrının hemen öncesine aşağıdaki kod satırını ekleyin (`TableAdapterManager.UpdateAll()` yöntemi):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)