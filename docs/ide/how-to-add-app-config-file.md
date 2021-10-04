---
title: Projeye app.config dosyası ekleme
description: Ortak dil çalışma zamanının derleme dosyalarını nasıl bulup yükleyebileceğinizi özelleştirebileceğiniz bir C# projesine bir app.config dosyası eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/20/2020
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
ms.openlocfilehash: 6c063aa1dbea8a9953bc3c9e44cf72de5514e0f8
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129431633"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Nasıl olur: C# projesine uygulama yapılandırma dosyası ekleme

Bir C# projesine bir *app.config* yapılandırma dosyası (dosya) ekleyerek, ortak dil çalışma zamanının derleme dosyalarını nasıl bulup yükley olduğunu özelleştirebilirsiniz. Uygulama yapılandırma dosyaları hakkında daha fazla bilgi için [bkz. Çalışma zamanı derlemeleri nasıl .NET Framework.](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)

> [!NOTE]
> UWP uygulamaları birapp.config *içermez.*

Projenizi derlemeniz sırasında geliştirme ortamı, *app.config* dosyanızı otomatik olarak kopyalar, kopyanın dosya adını yürütülebilir dosyanıza göre değiştirir ve ardından kopyayı **bin dizinine** taşır.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Bir C# projesine uygulama yapılandırma dosyası eklemek için

1. Menü çubuğunda Yeni Öğe **Ekle'Project**  >  **seçin.**

     **Yeni Öğe Ekle** iletişim kutusu görünür.

1. Yüklü **Visual**  >  **C# Öğeleri'ne genişletin** ve ardından Uygulama Yapılandırma Dosyası **şablonunu** seçin.

1. Ad **metin** kutusuna bir ad girin ve ekle **düğmesini** seçin.

     Projenize *app.config* adlı bir dosya eklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama ayarlarını yönetme (.NET)](../ide/managing-application-settings-dotnet.md)
- [Yapılandırma dosyası şeması (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Uygulamaları yapılandırma (.NET Framework)](/dotnet/framework/configure-apps/index)
