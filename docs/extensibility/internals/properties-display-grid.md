---
title: Özellikler Display Grid | Microsoft Docs
description: Özellik adları ve özellik değerleri alanlarının tablo içinde kılavuzda nerede Özellikler penceresi ve özellikleri genişletmede kılavuzla nasıl çalışabilirsiniz?
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
ms.openlocfilehash: d6ed5ce8863cef32c787d86a5d78c423d78fef4f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636134"
---
# <a name="properties-display-grid"></a>Özellikler görüntüleme kılavuzu

Özellikler **penceresinde** bir kılavuz içindeki alanlar görüntülenir. Sol sütun özellik adlarını içerir; sağ sütun özellik değerlerini içerir.

## <a name="work-with-the-grid"></a>Kılavuzla çalışma

İki sütunlu liste, tasarım zamanında değiştirilene yapılandırmadan bağımsız özellikleri ve bunların geçerli ayarlarını gösterir. Tüm özelliklerin gösterilmeyebilirsiniz. Bir özellik, örneğin yöntemi uygulanarak gizli olarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> ayarlanabilirsiniz. Özellikle, alt özellikleri olan özellikleri gizlemek için:

1. parametresini `pfDisplay` olarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> `FALSE` ayarlayın.

2. parametresini `pfHide` olarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> `TRUE` ayarlayın.

Özellikler penceresine bilgi **itmek** için IDE <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> kullanır. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>, Özellikler penceresinde görüntülenecek ilgili özelliklere sahip seçilebilir nesneleri içeren her pencere için VSPackages tarafından **çağrılır.** **Çözüm Gezgini** kullanarak çağrıların <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> uygulanmasını `GetProperty` [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) göz atılabilir nesneleri almak için proje hiyerarşinize göz atabilirsiniz.

VSPackage'nız bu desteği [__VSHPROPID. VSHPROPID_BrowseObject,](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>)IDE, IDE'nin <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) öğenin veya öğelerin temini için kullanılır.

Projenizin VSPackage'ını oluşturması gerekli değildir çünkü bunu uygulayan IDE tarafından sağlanan pencere paketi <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (örneğin, **Çözüm Gezgini**) kendi <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> adına yapılar.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , IDE tarafından çağrılan üç yöntemden oluşur:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> , Özellikler penceresinde görüntülenecek seçilen nesne **sayısını** içerir.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>, `IDispatch` Özellikler penceresinde görüntülenmek üzere  seçilen nesneleri döndürür.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> tarafından döndürülen nesnelerin kullanıcı tarafından <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> seçilmelerini mümkün yapar. Bu, VSPackage'ın kullanıcı arabiriminde görüntülenen seçimi görsel olarak güncelleştirmesini sağlar.

Özellikler **penceresi,** göz atlanan özellikleri `IDispatch` almak için nesnelerden bilgileri ayıklar. Özellikler tarayıcısı, `IDispatch` nesnesine, 'den alınan sorgusunu kullanarak hangi `ITypeInfo` özellikleri desteklediğini sormak için `IDispatch::GetTypeInfo` kullanır. Tarayıcı daha sonra özellikler penceresini doldurmak ve **kılavuzda** görüntülenen tek tek özelliklerin değerlerini değiştirmek için bu değerleri kullanır. Özellikler bilgileri nesnenin içinde korunur.

Döndürülen nesneler desteklemesi nedeniyle çağıranı, istenen bilgileri temsil eden önceden tanımlanmış bir gönderme tanımlayıcısı `IDispatch` (DISPID) ile çağırarak nesnenin adı gibi `IDispatch::Invoke` `ITypeInfo::Invoke` bilgileri elde eder. Bildirilen DISPID'ler, kullanıcı tanımlı tanımlayıcılarla çakışmamalarını sağlamak için negatiftir.

Özellikler **penceresi,** seçilen bir nesnenin belirli özelliklerinin özniteliklerine bağlı olarak farklı alan türlerini görüntüler. Bu alanlar düzenleme kutularını, açılan listeleri ve özel düzenleyici iletişim kutularının bağlantılarını içerir.

- Numaralandı listesinde yer alan değerler, sorgusu tarafından <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> `IDispatch` alınır. Listelenmiş bir listeden alınan değerler, alan adına çift tıklar veya değere tıklar ve açılır listeden yeni değer seçerek özellikler kılavuzunda değiştirilebilir. Numaralandı listelerden önceden tanımlanmış ayarlara sahip özellikler için, Özellikler listesinde özellik adına çift tıklar, kullanılabilir seçenekler arasında döngüler gösterir. Yalnızca iki seçeneği (true/false gibi) önceden tanımlanmış özellikler için, seçenekler arasında geçiş yapmak için özellik adına çift tıklayın.

- ise, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> `false` değerin değiştirdiğini belirtirse, değer kalın metin olarak görüntülenir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> değerin özgün değere sıfırlanabilir olup olmadığını belirlemek için kullanılır. Öyleyse, değere sağ tıklar ve görüntülenen menüden Sıfırla'yı seçerek **varsayılan** değere geri dönebilirsiniz. Aksi takdirde, değeri el ile varsayılan değere geri dönmeniz gerekir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> ayrıca tasarım zamanında görüntülenen özelliklerin adlarını yerelleştirmeye ve gizlemeye olanak sağlar, ancak çalışma zamanında görüntülenen özellik adlarını etkilemez.

- Üç nokta (...) düğmesine tıklarken, kullanıcının seçerek seçeci (renk seçici veya yazı tipi listesi gibi) özellik değerlerinin bir listesi görüntülenir. <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> bu değerleri sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Özellikleri genişletme](../../extensibility/internals/extending-properties.md)
