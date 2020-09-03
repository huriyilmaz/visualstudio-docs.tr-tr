---
title: Visual Studio 'da hiyerarşiler | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cdbb8a0e58f6b1e5bc6e32f8c319d1480c4db4b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708185"
---
# <a name="hierarchies-in-visual-studio"></a>Visual Studio’da Hiyerarşiler
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Tümleşik geliştirme ortamı (IDE) bir projeyi *hiyerarşi*olarak görüntüler. IDE 'de hiyerarşi, her düğümün ilişkili özellikler kümesi olduğu düğüm ağacıdır. *Proje hiyerarşisi* projenin öğelerini, öğelerin ilişkilerini ve öğelerin ilişkili özelliklerini ve komutlarını tutan bir kapsayıcıdır.

 İçinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , hiyerarşi arabirimini kullanarak proje hiyerarşilerini yönetirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>Arabirim, Proje öğelerinden çağırma komutlarını standart komut işleyicisi yerine uygun hiyerarşi penceresine yeniden yönlendirir.

## <a name="project-hierarchies"></a>Proje hiyerarşileri
 Her proje hiyerarşisi, görüntüleyebileceğiniz ve düzenleyebileceğiniz öğeleri içerir. Bu öğeler proje türüne göre farklılık gösterir. Örneğin, bir veritabanı projesi saklı yordamlar, veritabanı görünümleri ve veritabanı tabloları içerebilir. Diğer yandan bir programlama dili projesi, büyük olasılıkla bit eşlemler ve iletişim kutuları için kaynak dosyaları ve kaynak dosyaları içerir. Hiyerarşiler iç içe olabilir, bu da bir proje hiyerarşisi oluştururken bazı ek esneklik sağlar.

 Yeni bir proje türü oluşturduğunuzda proje türü, içinde düzenlenebilecek öğelerin tüm kümesini denetler. Ancak projeler, düzen desteği olmayan öğeler içerebilir. Örneğin, Visual C++, HTML dosya türü için özelleştirilmiş bir düzenleyici sağlamasa bile, Visual C++ projeler HTML dosyaları içerebilir.

 Hiyerarşiler içerdikleri öğelerin kalıcılığını yönetir. Hiyerarşinin uygulanması, hiyerarşideki öğelerin kalıcılığını etkileyen özel özellikleri denetmelidir. Örneğin, öğeler dosyalar yerine bir depodaki nesneleri temsil ediyorsa, hiyerarşi uygulamasının bu nesnelerin kalıcılığını denetmesi gerekir. IDE, öğeleri Kullanıcı girişiyle uyumlu olarak kaydetmek için hiyerarşiyi yönlendirir, ancak IDE, bu öğeleri kaydetmek için gereken herhangi bir eylemi denetlemez. Bunun yerine, proje denetimde olur.

 Bir Kullanıcı düzenleyicide bir öğeyi açtığında, bu öğeyi denetleyen hiyerarşi seçilir ve etkin hiyerarşi haline gelir. Seçili hiyerarşi, öğede işlem yapması için kullanılabilen komut kümesini belirler. Kullanıcı odağı bu şekilde izlemek, hiyerarşinin kullanıcının geçerli içeriğini yansıtmasını sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje türleri](../../extensibility/internals/project-types.md)
- [IDE 'de seçim ve para birimi](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [VSSDK örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
