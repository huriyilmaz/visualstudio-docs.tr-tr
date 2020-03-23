---
title: Şablondan bir AI projesi oluşturma
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 0b537d80b8db9150c6804aff2ee3de0e6c879bb9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62546745"
---
# <a name="create-an-ai-project-from-a-template-in-visual-studio"></a>Visual Studio'daki şablondan bir AI projesi oluşturma

[AI için Visual Studio Tools'u yükledikten](installation.md)sonra, çeşitli şablonlar kullanarak yeni bir AI projesi oluşturmak kolaydır.

1. Visual Studio’yu başlatın.

2. **Yeni > Projesi> Dosya'yı** (Ctrl+Shift+N) seçin. Yeni **Proje** iletişim kutusunda , "**AI Araçları**" için arama yapın ve istediğiniz şablonu seçin. Şablon seçmenin şablonun sağladığı kısa bir açıklamayı görüntülediğini unutmayın.

    ![PYTHON şablonu ile VS2017 Yeni Proje iletişim kutusu](media/create-project/new-ai-project.png)

3. Bu Quickstart için "**TensorFlow Application**" şablonu'nu seçin, projeye bir ad ("MNIST" gibi) ve konum verin ve **Tamam'ı**seçin.

4. Visual Studio, şablontarafından açıklandığı `.pyproj` gibi diğer dosyalarla birlikte proje dosyasını (diskteki bir dosya) oluşturur. "TensorFlow Application" şablonuyla proje, projenizle aynı adlı bir dosya içerir. Dosya varsayılan olarak Visual Studio düzenleyicisinde açıktır.

    ![Python Application şablonunu kullanırken ortaya çıkan proje](media/create-project/new-tensorflowapp.png)

5. Kodun zaten TensorFlow, numpy, sys ve os dahil olmak üzere çeşitli kütüphaneler alır unutmayın. Ayrıca, giriş eğitim verilerinin, çıktı modellerinin ve günlük dosyalarının konumunu kolayca değiştirmeyi etkinleştirmek için uygulamanızı bazı giriş bağımsız değişkenleriyle hazır hale getirerek başlatır. Bu paramlar, işlerinizi birden çok bilgi işlem bağlamına (yani yerel dev kutunuzda Azure Dosya Paylaşımı'ndakinden farklı dizin) gönderdiğinizde yararlıdır.

6. Projenizde, komut satırı bağımsız değişkenlerini bu giriş parametrelerine otomatik olarak geçirerek uygulamanızın hata sını kolayca ayıklamayı kolaylaştırmak için oluşturulan bazı özellikler de vardır. Projenizi **sağ tıklatın** ve **Özellikler'i** seçin

    ![Özellikler](media/create-project/project-properties.png)

7. Komut Dosyası Bağımsız Değişkenlerini otomatik olarak eklenenleri görmek için **Hata Ayıklama** sekmesini tıklatın. bunları gerektiğinde giriş verilerinizin bulunduğu ve çıktınızın depolanmış olmasını istediğiniz yere değiştirebilirsiniz.

    ![Özellikler](media/create-project//project-properties_1.png)

8. Ctrl+F5 tuşuna basarak veya menüde Hata **Ayıklama olmadan Başlat > Hata** Ayıklama'yı seçerek programı çalıştırın. Sonuçlar bir konsol penceresinde görüntülenir.
