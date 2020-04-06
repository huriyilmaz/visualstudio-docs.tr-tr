---
title: Visual Studio'da Hiyerarşiler | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708185"
---
# <a name="hierarchies-in-visual-studio"></a>Visual Studio’da Hiyerarşiler
Tümleşik [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geliştirme ortamı (IDE) bir projeyi *hiyerarşi*olarak görüntüler. IDE'de hiyerarşi, her düğümün ilişkili özelliklerinin olduğu bir düğüm ağacıdır. *Proje hiyerarşisi,* projenin öğelerini, öğelerin ilişkilerini ve öğelerin ilişkili özelliklerini ve komutlarını tutan bir kapsayıcıdır.

 , [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]hiyerarşi arabirimini kullanarak proje hiyerarşilerini <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>yönetirsiniz. Arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> proje öğelerinden çağırdığınız komutları standart komut işleyicisi yerine uygun hiyerarşi penceresine yönlendirir.

## <a name="project-hierarchies"></a>Proje hiyerarşileri
 Her proje hiyerarşisi görüntüleyebilir ve edinebileceğiniz öğeler içerir. Bu öğeler proje türüne bağlı olarak değişir. Örneğin, bir veritabanı projesi depolanmış yordamlar, veritabanı görünümleri ve veritabanı tabloları içerebilir. Öte yandan, programlama dili projesi büyük olasılıkla bit eşlemler ve iletişim kutuları için kaynak dosyaları ve kaynak dosyaları içerecektir. Hiyerarşiler iç içe olabilir ve bu da proje hiyerarşisi oluşturduğunuzda size bazı ek esneklikler sağlar.

 Yeni bir proje türü oluşturduğunuzda, proje türü içinde düzenlenebilen tüm öğe kümesini denetler. Ancak, projeler için düzenleme desteği olmayan öğeler içerebilir. Örneğin, Visual C++ HTML dosya türü için özelleştirilmiş bir düzenleyici sağlamasa da, Visual C++ projeleri HTML dosyaları içerebilir.

 Hiyerarşiler içerdikleri öğelerin kalıcılığını yönetir. Hiyerarşinin uygulanması, hiyerarşi içindeki öğelerin kalıcılığını etkileyen özel özellikleri denetlemelidir. Örneğin, öğeler dosyalar yerine bir depodaki nesneleri temsil ediyorsa, hiyerarşi uygulamasının bu nesnelerin kalıcılığını denetlemesi gerekir. IDE'nin kendisi, öğeleri kullanıcı girişiyle uyumlu olarak kaydetmek için hiyerarşiyi yönlendirir, ancak IDE bu öğeleri kaydetmek için gereken eylemleri denetlemez. Bunun yerine, proje kontrol altındadır.

 Bir kullanıcı bir düzenleyicide bir öğe açtığında, bu öğeyi denetleyen hiyerarşi seçilir ve etkin hiyerarşi olur. Seçili hiyerarşi, öğe üzerinde hareket etmek için kullanılabilir komutkümesini belirler. Kullanıcı odağının bu şekilde izlenmesi, hiyerarşinin kullanıcının geçerli bağlamını yansıtmasını sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje türleri](../../extensibility/internals/project-types.md)
- [IDE'de seçim ve para birimi](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [VSSDK örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
