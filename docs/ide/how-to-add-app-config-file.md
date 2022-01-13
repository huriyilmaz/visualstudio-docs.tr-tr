---
title: Projeye app.config dosyası ekleme
description: Ortak dil çalışma zamanının derleme dosyalarını nasıl bulup yükleyebileceğinizi özelleştirebileceğiniz bir C# projesine bir app.config dosyası eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/12/2022
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 426750ded6c14dfc2015bfc5ab1e8b73d92eaa88
ms.sourcegitcommit: 9b1c1cceab4c59f0b91e19ae46a51969f72fcc34
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2022
ms.locfileid: "136801233"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Nasıl olur: C# projesine uygulama yapılandırma dosyası ekleme

Bir C# projesine bir *uygulamaapp.config* dosyası ekleyerek , ortak dil çalışma zamanının derleme dosyalarını bulma ve yüklemesini özelleştirebilirsiniz. Uygulama yapılandırma dosyaları hakkında daha fazla bilgi için [bkz. Çalışma zamanı derlemeleri nasıl .NET Framework.](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)

> [!NOTE]
> UWP uygulamaları birapp.config *içermez.*

Projenizi derlemeniz sırasında geliştirme ortamı app.configdosyanızı otomatik olarak kopyalar, kopyanın dosya adını yürütülebilir dosyanıza göre değiştirir ve ardından kopyayı **bin dizinine** taşır.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Bir C# projesine uygulama yapılandırma dosyası eklemek için

::: moniker range="vs-2017"

1. Menü çubuğunda Yeni Öğe **Ekle'Project** > **seçin.**

     **Yeni Öğe Ekle** iletişim kutusu görünür.

1. Yüklü **Visual** > **C# Öğeleri'ne genişletin** ve ardından Uygulama Yapılandırma Dosyası **şablonunu** seçin.

1. Ad **metin** kutusuna bir ad girin ve ekle **düğmesini** seçin.

     projenize *app.config* adlı bir dosya eklenir.

::: moniker-end

::: moniker range=">=vs-2019"

1. Bu **Çözüm Gezgini** proje düğümüne sağ tıklayın ve Ardından Yeni Öğe **Ekle'yi** > **seçin.**

     **Yeni Öğe Ekle** iletişim kutusu görünür.

1. Yüklü **Visual** > **C# Öğeleri'ne genişletin.**

1. Orta bölmede Uygulama Yapılandırma **Dosyası şablonunu** seçin.

1. Ekle **düğmesini** seçin.

     projenize *App.config* adlı bir dosya eklenir.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama ayarlarını yönetme (.NET)](../ide/managing-application-settings-dotnet.md)
- [Yapılandırma dosyası şeması (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Uygulamaları yapılandırma (.NET Framework)](/dotnet/framework/configure-apps/index)
