---
title: Bir projeye app.config dosya ekleme
description: Ortak dil çalışma zamanının derleme dosyalarını nasıl bulup yüklediğini özelleştirmek için bir C# projesine app.config dosyası eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 282c66acd71d0c68ff5bc3c74db2e8a2517a00d1
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597361"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Nasıl yapılır: C# projesine uygulama yapılandırma dosyası ekleme

Bir C# projesine uygulama yapılandırma dosyası (*app.config* dosyası) ekleyerek, ortak dil çalışma zamanının derleme dosyalarını nasıl bulup yüklediğini özelleştirebilirsiniz. Uygulama yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> UWP uygulamaları *app.config* bir dosya içermez.

Projenizi oluşturduğunuzda, geliştirme ortamı *app.config* dosyanızı otomatik olarak kopyalar, kopyanın dosya adını çalıştırılabilirle eşleşecek şekilde değiştirir ve ardından kopyayı **bin** dizinine taşımalıdır.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Bir C# projesine uygulama yapılandırma dosyası eklemek için

1. Menü çubuğunda, **Proje**  >  **Yeni öğe Ekle**' yi seçin.

     **Yeni Öğe Ekle** iletişim kutusu görünür.

1. **Yüklü**  >  **Visual C# öğelerini** genişletin ve ardından **uygulama yapılandırma dosyası** şablonunu seçin.

1. **Ad** metin kutusuna bir ad girin ve sonra **Ekle** düğmesini seçin.

     *app.config* adlı bir dosya projenize eklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama ayarlarını yönetme (.NET)](../ide/managing-application-settings-dotnet.md)
- [Yapılandırma dosyası şeması (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Uygulamaları yapılandırma (.NET Framework)](/dotnet/framework/configure-apps/index)
