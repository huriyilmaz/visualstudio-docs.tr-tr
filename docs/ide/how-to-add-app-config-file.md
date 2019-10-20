---
title: Projeye bir App. config dosyası ekleme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 48e6516b48b524c3da4d80bc5171608ac1aea03d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654259"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Nasıl yapılır: bir C# projeye uygulama yapılandırma dosyası ekleme

Bir C# projeye uygulama yapılandırma dosyası (*app. config* dosyası) ekleyerek, ortak dil çalışma zamanının derleme dosyalarını nasıl bulup yüklediğini özelleştirebilirsiniz. Uygulama yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> UWP uygulamaları bir *app. config* dosyası içermez.

Projenizi oluşturduğunuzda, geliştirme ortamı *app. config* dosyanızı otomatik olarak kopyalar, kopyanın dosya adını çalıştırılabilirle eşleşecek şekilde değiştirir ve ardından kopyayı **bin** dizinine taşımalıdır.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Bir C# projeye uygulama yapılandırma dosyası eklemek için

1. Menü çubuğunda, **proje**  > **Yeni öğe Ekle**' yi seçin.

     **Yeni öğe Ekle** iletişim kutusu görüntülenir.

1. **Yüklü**  > **görsel C# öğelerini**genişletin ve ardından **uygulama yapılandırma dosyası** şablonunu seçin.

1. **Ad** metin kutusuna bir ad girin ve sonra **Ekle** düğmesini seçin.

     Projenize *app. config* adlı bir dosya eklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama ayarlarını yönetme (.NET)](../ide/managing-application-settings-dotnet.md)
- [Yapılandırma dosyası şeması (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Uygulamaları yapılandırma (.NET Framework)](/dotnet/framework/configure-apps/index)