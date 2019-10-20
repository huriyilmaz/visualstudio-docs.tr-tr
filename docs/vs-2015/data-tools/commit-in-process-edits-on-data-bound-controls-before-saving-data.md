---
title: Veri kaydedilmeden önce veri bağlantılı denetimlerde işlem içi düzenlemeleri işleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3867b91a8b417b5670514b66aaf93fdab4e9618c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662459"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Verileri kaydetmeden önce verilere bağlı denetimler üzerinde işlem içi düzenlemeler yürütme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veri bağlantılı denetimlerde değerler düzenlenirken, kullanıcılar, güncelleştirilmiş değeri denetimin bağlandığı temel alınan veri kaynağına uygulamak için geçerli kaydın üzerinde gezinmelidir. Öğeleri [veri kaynakları penceresinden](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) bir form üzerine sürüklediğinizde, sürüklediğiniz ilk öğe <xref:System.Windows.Forms.BindingNavigator> **Kaydet** düğmesi tıklama olayına kodu oluşturur. Bu kod, <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemini çağırır. Bu nedenle, <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemine yapılan çağrı yalnızca forma eklenen ilk <xref:System.Windows.Forms.BindingSource> için oluşturulur.

 @No__t_0 çağrısı, şu anda düzenlenmekte olan herhangi bir veri bağlantılı denetimlerde, işlemdeki tüm değişiklikleri kaydeder. Bu nedenle, veri bağlantılı bir denetim hala odağa sahipse ve **Kaydet** düğmesine tıklarsanız, bu denetimdeki tüm bekleyen düzenlemeler gerçek kaydetme işleminden önce (`TableAdapterManager.UpdateAll` yöntemi) kaydedilir.

 Bir Kullanıcı, değişiklikleri kaydetmeden, kaydetme işleminin bir parçası olarak verileri kaydetmeye çalışırsa bile, uygulamanızı otomatik olarak değişiklikleri işleyecek şekilde yapılandırabilirsiniz.

> [!NOTE]
> Tasarımcı, yalnızca bir forma bırakılan ilk öğe için `BindingSource.EndEdit` kodunu ekler. Bu nedenle, formdaki her bir <xref:System.Windows.Forms.BindingSource> için <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemini çağırmak üzere bir kod satırı eklemeniz gerekir. Her <xref:System.Windows.Forms.BindingSource> için <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemini çağırmak üzere bir kod satırı el ile ekleyebilirsiniz. Alternatif olarak, `EndEditOnAllBindingSources` yöntemini forma ekleyebilir ve kaydetme işlemini gerçekleştirmeden önce bu yöntemi çağırabilirsiniz.

 Aşağıdaki kod, tüm <xref:System.Windows.Forms.BindingSource> bileşenlerini yinelemek ve bir formdaki her <xref:System.Windows.Forms.BindingSource> için <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemini çağırmak üzere bir [LINQ (dil Ile tümleşik sorgu)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) sorgusu kullanır.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Form üzerindeki tüm BindingSource bileşenleri için EndEdit 'u çağırmak için

1. Aşağıdaki kodu <xref:System.Windows.Forms.BindingSource> bileşenleri içeren forma ekleyin.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#1)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#1)]

2. Form verilerini kaydetmek için herhangi bir çağrının hemen öncesine aşağıdaki kod satırını ekleyin (`TableAdapterManager.UpdateAll()` yöntemi):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#2)]

## <a name="see-also"></a>Ayrıca Bkz.
 Visual Studio [hiyerarşik güncelleştirmesinde](../data-tools/hierarchical-update.md) [Windows Forms denetimleri verilere bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
