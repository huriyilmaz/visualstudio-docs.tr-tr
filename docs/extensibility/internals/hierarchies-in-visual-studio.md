---
title: Visual Studio |'de hiyerarşiler Microsoft Docs
description: Proje öğelerini ve ilişkili özelliklerini içeren Visual Studio geliştirme ortamındaki (IDE) proje hiyerarşileri hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3d8058091742f8e0f9ed3e51ebf0d046ee1524e5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725065"
---
# <a name="hierarchies-in-visual-studio"></a>Visual Studio’da Hiyerarşiler
Tümleşik [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geliştirme ortamı (IDE), bir projeyi hiyerarşi olarak *görüntüler.* IDE'de hiyerarşi, her düğümün ilişkili özellikler kümesine sahip olduğu bir düğüm ağacıdır. Proje *hiyerarşisi,* projenin öğelerini, öğelerin ilişkilerini ve öğelerin ilişkili özelliklerini ve komutlarını tutan bir kapsayıcıdır.

 içinde, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje hiyerarşilerini hiyerarşi arabirimini kullanarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> yönetirsiniz. Arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> proje öğelerinden çağıran komutları standart komut işleyicisi yerine uygun hiyerarşi penceresine yeniden yönlendiriyor.

## <a name="project-hierarchies"></a>Project hiyerarşileri
 Her proje hiyerarşisi, görüntüleyemez ve düzenleyemezsiniz öğeleri içerir. Bu öğeler proje türüne göre değişiklik gösterir. Örneğin, bir veritabanı projesi saklı yordamlar, veritabanı görünümleri ve veritabanı tabloları içerebilir. Diğer taraftan bir programlama dili projesi büyük olasılıkla bit eşlemler ve iletişim kutuları için kaynak dosyaları ve kaynak dosyaları içerir. Hiyerarşiler iç içe geçmiş olabilir ve bu da bir proje hiyerarşisi oluşturma konusunda daha fazla esneklik sunar.

 Yeni bir proje türü oluşturma işlemi, proje türü içinde düzenlenemez tüm öğe kümelerini kontrol eder. Ancak projeler, düzenleme desteğine sahip olmadığınız öğeler içerebilir. Örneğin, Visual C++ projeleri HTML dosyaları içerebilir, ancak Visual C++ html dosya türü için özelleştirilmiş bir düzenleyici sağlamaz.

 Hiyerarşiler, içerecekleri öğelerin kalıcılıklarını yönetir. Hiyerarşinin uygulanması, hiyerarşi içindeki öğelerin kalıcılıklarını etkileyen tüm özel özellikleri denetlemeli. Örneğin, öğeler dosyalar yerine bir depodaki nesneleri temsil ediyorsa, hiyerarşi uygulaması bu nesnelerin kalıcılık denetimine sahip olmalıdır. IDE, hiyerarşiyi öğeleri kullanıcı girişiyle uyumlu olarak kaydetmeye yönlendirmektedir, ancak IDE bu öğeleri kaydetmek için gereken eylemleri denetlemez. Bunun yerine, proje denetimdedir.

 Kullanıcı bir düzenleyicide bir öğe açtığında, bu öğeyi kontrol eden hiyerarşi seçilir ve etkin hiyerarşi olur. Seçilen hiyerarşi, öğe üzerinde eyleme geçilecek komutlar kümesi belirler. Kullanıcı odağında bu şekilde izleme, hiyerarşinin kullanıcının geçerli bağlamını yansıtması sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [Project türleri](../../extensibility/internals/project-types.md)
- [IDE'de seçim ve para birimi](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [VSSDK örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
