---
title: Projeye app.config dosyası nasıl eklenir?
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3eb813dc5d4389b002851a904d61219b0d5c316e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593648"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Nasıl yapilir: C# projesine uygulama yapılandırma dosyası ekleme

C# projesine bir uygulama yapılandırma dosyası *(app.config* dosyası) ekleyerek, ortak dil çalışma zamanının derleme dosyalarını nasıl bulup yüklerini özelleştirebilirsiniz. Uygulama yapılandırma dosyaları hakkında daha fazla bilgi için [çalışma zamanının derlemeleri (.NET Framework) nasıl bulabildiğini](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)öğrenin.

> [!NOTE]
> UWP uygulamaları bir *app.config* dosyası içermez.

Projenizi oluşturduğunuzda, geliştirme ortamı uygulamanızı otomatik olarak *kopyalar.config* dosyanızı kopyalar, kopyanın dosya adını yürütülebilir dosyanızla eşleşecek şekilde değiştirir ve kopyayı **depo** gözü dizine taşır.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>C# projesine uygulama yapılandırma dosyası eklemek için

1. Menü çubuğunda **Project** > **Add New Item'i**seçin.

     **Yeni Öğe Ekle** iletişim kutusu görünür.

1. **Yüklü** > **Görsel C# Öğelerini**genişletin ve ardından **Uygulama Yapılandırma Dosyası** şablonuna bakın.

1. **Ad** metin kutusuna bir ad girin ve sonra **Ekle** düğmesini seçin.

     projenize *app.config* adlı bir dosya eklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama ayarlarını yönetme (.NET)](../ide/managing-application-settings-dotnet.md)
- [Yapılandırma dosyası şeması (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Uygulamaları yapılandırma (.NET Framework)](/dotnet/framework/configure-apps/index)
