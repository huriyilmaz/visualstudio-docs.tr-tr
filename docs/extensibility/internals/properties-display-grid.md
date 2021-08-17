---
title: Özellikler Kılavuz | Microsoft Docs
description: Özellik adlarının ve özellik değerlerinin alanlarının Özellikler penceresi kılavuzda nerede olduğunu ve özellikleri genişletmede kılavuzla nasıl çalışıı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f9186d9c912f27ec1e782eb4c6e48de3b340a6c1fadbb711cc7c2db02ef7ab5d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401316"
---
# <a name="properties-display-grid"></a>Özellikler görüntüleme kılavuzu

Özellikler **penceresinde** bir kılavuz içindeki alanlar görüntülenir. Sol sütun özellik adlarını içerir; sağ sütun özellik değerlerini içerir.

## <a name="work-with-the-grid"></a>Kılavuzla çalışma

İki sütunlu liste, tasarım zamanında ve geçerli ayarlarında değiştirilene yapılandırmadan bağımsız özellikleri gösterir. Tüm özelliklerin gösterilmeyebilirsiniz. Bir özellik, örneğin yöntemi uygulanarak gizli olarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> ayarlanabilirsiniz. Özellikle, alt özellikleri olan özellikleri gizlemek için:

1. içinde `pfDisplay` parametresini olarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> `FALSE` ayarlayın.

2. içinde `pfHide` parametresini olarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> `TRUE` ayarlayın.

Özellikler penceresine bilgi **itmek** için IDE <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> kullanır. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>, Özellikler penceresinde görüntülenecek ilgili özelliklere sahip seçilebilir nesneleri içeren her pencere için VSPackages tarafından **çağrılır.** **Çözüm Gezgini** kullanarak <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> çağrıların `GetProperty` uygulanmasını [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) göz atılabilir nesneleri almak için proje hiyerarşinize göz atabilirsiniz.

VSPackage'nız bu desteği [__VSHPROPID. VSHPROPID_BrowseObject,](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>)IDE, IDE'nin <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) öğenin veya öğelerin temini için kullanılır.

Projenizin VSPackage'ını oluşturması gerekli değildir çünkü bunu uygulayan IDE tarafından sağlanan pencere paketi <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (örneğin, **Çözüm Gezgini**) kendi <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> adına yapılarıdır.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , IDE tarafından çağrılan üç yöntemden oluşur:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> , Özellikler penceresinde görüntülenecek seçilen nesne **sayısını** içerir.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>, `IDispatch` Özellikler penceresinde görüntülenmek üzere  seçilen nesneleri döndürür.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> tarafından döndürülen nesnelerin kullanıcı tarafından <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> seçilmelerini mümkün yapar. Bu, VSPackage'ın kullanıcı arabiriminde görüntülenen seçimi görsel olarak güncelleştirmesini sağlar.

Özellikler **penceresi,** göz atlanan `IDispatch` özellikleri almak için nesnelerden bilgileri ayıklar. Özellikler tarayıcısı `IDispatch` nesnesine, 'den alınan sorgusunu kullanarak hangi `ITypeInfo` özellikleri desteklediğini sormak için `IDispatch::GetTypeInfo` kullanır. Ardından tarayıcı, Özellikler penceresini doldurmak ve **kılavuzda** görüntülenen tek tek özelliklerin değerlerini değiştirmek için bu değerleri kullanır. Özellikler bilgileri nesnenin içinde korunur.

Döndürülen nesneler desteklemesi nedeniyle çağıranı, istenen bilgileri temsil eden önceden tanımlanmış bir gönderme tanımlayıcısı `IDispatch` (DISPID) ile çağırarak nesnenin adı gibi `IDispatch::Invoke` `ITypeInfo::Invoke` bilgileri elde eder. Bildirilen DISPID'ler, kullanıcı tanımlı tanımlayıcılarla çakışmamalarını sağlamak için negatiftir.

Özellikler **penceresi,** seçilen bir nesnenin belirli özelliklerinin özniteliklerine bağlı olarak farklı alan türlerini görüntüler. Bu alanlar düzenleme kutularını, açılan listeleri ve özel düzenleyici iletişim kutularının bağlantılarını içerir.

- Numaralandı listesinde yer alan değerler, sorgusu tarafından <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> olarak `IDispatch` alınır. Listelenmiş bir listeden alınan değerler, alan adına çift tıklayarak veya değere tıklar ve açılır listeden yeni değer seçerek özellikler kılavuzunda değiştirilebilir. Numaralandı listelerden önceden tanımlanmış ayarlara sahip özellikler için Özellikler listesinde özellik adına çift tıklar, kullanılabilir seçenekler arasında döngüye gelir. Yalnızca iki seçeneği (true/false gibi) önceden tanımlanmış özellikler için, seçenekler arasında geçiş yapmak için özellik adına çift tıklayın.

- ise, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> `false` değerin değiştirdiğini belirtirse, değer kalın metin olarak görüntülenir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> değerin özgün değere sıfırlanabilir olup olmadığını belirlemek için kullanılır. Öyleyse, değere sağ tıklar ve görüntülenen menüden Sıfırla'yı **seçerek varsayılan** değere geri dönebilirsiniz. Aksi takdirde, değeri el ile varsayılan değere geri dönmeniz gerekir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> ayrıca tasarım zamanında görüntülenen özelliklerin adlarını yerelleştirmeye ve gizlemeye olanak sağlar, ancak çalışma zamanında görüntülenen özellik adlarını etkilemez.

- Üç nokta (...) düğmesine tıklarken, kullanıcının seçerek seçebiliyor olduğu özellik değerlerinin (renk seçici veya yazı tipi listesi gibi) listesi görüntülenir. <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> bu değerleri sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Özellikleri genişletme](../../extensibility/internals/extending-properties.md)
