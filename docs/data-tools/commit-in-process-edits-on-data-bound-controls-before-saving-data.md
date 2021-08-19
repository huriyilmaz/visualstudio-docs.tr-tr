---
title: İşlenemez düzenlemeler
description: Verileri kaydetmeden önce, veriye bağlı Windows Formlar denetimlerini işleme. Bir formda tüm BindingSource bileşenleri için EndEdit çağrısı.
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
ms.openlocfilehash: 9e69734b43a0c959a724ee9116f919597c14002d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154933"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Verileri kaydetmeden önce verilere bağlı denetimler üzerinde işlem içi düzenlemeler yürütme

Veriye bağlı denetimlerde değerleri düzenlerken, kullanıcıların güncelleştirilmiş değeri denetimin bağlı olduğu temel alınan veri kaynağına kaydetmek için geçerli kayıttan inmiş olması gerekir. Veri Kaynakları Penceresindeki [öğeleri](add-new-data-sources.md) bir forma sürüklerken, bıraktığınızda ilk öğe Kaydet düğmesine **tıklayarak** olayına kod <xref:System.Windows.Forms.BindingNavigator> üretir. Bu kod yöntemini <xref:System.Windows.Forms.BindingSource.EndEdit%2A> <xref:System.Windows.Forms.BindingSource> çağıran. Bu nedenle, <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemine yapılan çağrı yalnızca forma <xref:System.Windows.Forms.BindingSource> eklenen ilk için oluşturulur.

Çağrısı, <xref:System.Windows.Forms.BindingSource.EndEdit%2A> devam eden tüm değişiklikleri, şu anda düzende olan veriye bağlı denetimlerde işler. Bu nedenle, veriye bağlı bir denetimin  odağı hala varsa ve Kaydet düğmesine tıklarsanız, bu denetimdeki bekleyen tüm düzenlemeler gerçek kaydetmeden önce (yöntem) `TableAdapterManager.UpdateAll` işlendi.

Kullanıcı değişiklikleri işlemeden verileri kaydetmeye çalışsa bile, kaydetme işleminin bir parçası olarak, değişiklikleri otomatik olarak işleyene kadar uygulamanızı yapılandırabilirsiniz.

> [!NOTE]
> Tasarımcı yalnızca `BindingSource.EndEdit` forma bırakılan ilk öğenin kodunu ekler. Bu nedenle, formda her biri için yöntemini çağıran <xref:System.Windows.Forms.BindingSource.EndEdit%2A> bir kod satırı eklemeniz <xref:System.Windows.Forms.BindingSource> gerekir. Her için yöntemini çağıran bir kod satırı el <xref:System.Windows.Forms.BindingSource.EndEdit%2A> ile <xref:System.Windows.Forms.BindingSource> ekleyebilirsiniz. Alternatif olarak, kaydetme işlemi `EndEditOnAllBindingSources` gerçekleştirmeden önce forma yöntemini ekleyebilir ve çağırabilirsiniz.

Aşağıdaki kod bir [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) sorgusu kullanarak tüm bileşenleri yeniden kullanır ve formda her <xref:System.Windows.Forms.BindingSource> biri için yöntemini <xref:System.Windows.Forms.BindingSource.EndEdit%2A> <xref:System.Windows.Forms.BindingSource> çağırabilir.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Bir formda tüm BindingSource bileşenleri için EndEdit çağrısı yapmak için

1. Bileşenleri içeren forma aşağıdaki kodu <xref:System.Windows.Forms.BindingSource> ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet1":::

2. Formun verilerini kaydetmek için çağrılardan hemen önce aşağıdaki kod satırı ekleyin `TableAdapterManager.UpdateAll()` (yöntemi):

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet2":::

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)
