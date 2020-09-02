---
title: 'Nasıl yapılır: C# projesine uygulama yapılandırma dosyası ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8417b5520dc9587fa3231a3bc459335d2a9896d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667526"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Nasıl yapılır: C# Projesine Uygulama Yapılandırma Dosyası Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir C# projesine uygulama yapılandırma dosyası (app.config dosyası) ekleyerek, ortak dil çalışma zamanının derleme dosyalarını nasıl bulup yüklediğini özelleştirebilirsiniz. Uygulama yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).

> [!NOTE]
> Windows Mağazası desteklemez <xref:System.Configuration> . Sonuç olarak, Mağaza uygulamaları app.config şablonu içermez.

 Projenizi oluşturduğunuzda, geliştirme ortamı app.config dosyanızı otomatik olarak kopyalar, kopyanın dosya adını çalıştırılabilirle eşleşecek şekilde değiştirir ve ardından kopyayı bin dizinine taşımalıdır.

### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>C# projenize bir uygulama yapılandırma dosyası eklemek için

1. Menü çubuğunda **Proje**, **Yeni öğe Ekle**' yi seçin.

     **Yeni Öğe Ekle** iletişim kutusu görünür.

2. **Yüklü**' i genişletin, **Visual C# öğeleri**' ni genişletin ve ardından **uygulama yapılandırma dosyası** şablonunu seçin.

3. **Ad** metin kutusuna bir ad girin ve sonra **Ekle** düğmesini seçin.

     app.config adlı bir dosya projenize eklenir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Uygulama ayarlarını yönetme (.net)](../ide/managing-application-settings-dotnet.md) [yapılandırma dosya şeması](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38) [uygulamaları yapılandırma](https://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f) nasıl yapılır: [C# için Visual Studio geliştirme ortamını kullanarak](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) [.NET Framework sürümünü hedeflemek için uygulama yapılandırma](https://msdn.microsoft.com/5247b307-89ca-417b-8dd0-e8f9bd2f4717)