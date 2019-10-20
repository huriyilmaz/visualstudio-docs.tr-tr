---
title: Verilere Windows Forms denetimleri bağlama
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
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a03f4df57b216fa68e5ac24df80b67917aa3e3f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672983"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere Windows Forms denetimleri bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verileri Windows Forms 'e bağlayarak uygulamanızın kullanıcılarına verileri görüntüleyebilirsiniz. Bu verilere dayalı denetimleri oluşturmak için, **veri kaynakları** penceresinden öğeleri Visual Studio 'daki Windows Form Tasarımcısı sürükleyebilirsiniz. Bu konuda, veri bağlantılı Windows Forms uygulamaları oluşturma ile ilgili en yaygın görevlerden, araçların ve sınıfların bazıları açıklanmaktadır.

 ![Veri kaynağı sürükleme işlemi](../data-tools/media/raddata-data-source-drag-operation.png "radveri veri kaynağı sürükleme işlemi")

 Visual Studio 'da verilere bağlı denetimler oluşturma hakkında genel bilgi için bkz. [Visual Studio 'da denetimleri verilere bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md). Windows Forms veri bağlama hakkında daha fazla bilgi için bkz. [Windows Forms veri bağlama](https://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa).

## <a name="in-this-section"></a>Bu bölümde

- [Verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data.md)

- [Verileri kaydetmeden önce verilere bağlı denetimler üzerinde işlem içi düzenlemeler yürütme](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)

- [Windows Forms uygulamalarında arama tabloları oluşturma](../data-tools/create-lookup-tables-in-windows-forms-applications.md)

- [Veri aramak için Windows Form oluşturma](../data-tools/create-a-windows-form-to-search-data.md)

- [Basit veri bağlama modelini destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)

- [Karmaşık veri bağlama modelini destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)

- [Arama veri bağlama modelini destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)

- [Formlar arasında veri geçirme](../data-tools/pass-data-between-forms.md)

## <a name="bindingsource-component"></a>BindingSource bileşeni
 @No__t_0 bileşeni iki amaca hizmet eder. İlk olarak, formunuzdaki denetimleri verilerle bağlarken bir soyutlama katmanı sağlar. Formdaki denetimler <xref:System.Windows.Forms.BindingSource> bileşene bağlıdır (doğrudan bir veri kaynağına bağlı olmak yerine).

 İkincisi, bir nesne koleksiyonunu yönetebilir. @No__t_0 bir türü eklemek, bu türün bir listesini oluşturur.

 @No__t_0 bileşeni hakkında daha fazla bilgi için bkz.:

- [BindingSource Bileşeni](https://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)

- [BindingSource Bileşenine Genel Bakış](https://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)

- [BindingSource Bileşeni Mimarisi](https://msdn.microsoft.com/library/7bc69c90-8a11-48b1-9336-3adab5b41591)

## <a name="bindingnavigator-control"></a>BindingNavigator denetimi
 Bu bileşen, bir Windows uygulaması tarafından gösterilecek veriler arasında gezinmek için bir kullanıcı arabirimi sağlar. Daha fazla bilgi için bkz. [BindingNavigator denetimi](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).

## <a name="datagridview-control"></a>DataGridView denetimi
 Birçok farklı türde veri kaynağından tablo verilerini göstermek ve düzenlemek için <xref:System.Windows.Forms.DataGridView> denetimini kullanın. @No__t_1 özelliğini kullanarak verileri <xref:System.Windows.Forms.DataGridView> bağlayabilirsiniz. Daha fazla bilgi için bkz. [DataGridView denetimine genel bakış](https://msdn.microsoft.com/library/0a45c661-89dc-4390-9cc6-c47eee501488).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
