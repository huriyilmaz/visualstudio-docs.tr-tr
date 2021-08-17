---
title: Şablondan AI projesi oluşturma
description: Çeşitli şablonlardan Visual Studio Araçları bir AI projesi oluşturmak için Visual Studio Araçları'yi kullanmayı öğrenin.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
ms.technology: vs-ai-tools
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: e1a9cbdd4449282076703134862178f3a866851f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122067731"
---
# <a name="create-an-ai-project-from-a-template-in-visual-studio"></a>Visual Studio'de şablondan bir AI projesi Visual Studio

AI için [Visual Studio Araçları'yi](installation.md)yüklemiş olduktan sonra, çeşitli şablonları kullanarak yeni bir AI projesi kolayca oluşturabilirsiniz.

1. Visual Studio.

2. Yeni **> (Ctrl+Shift+N)** > Project'yi seçin. Yeni **Project** iletişim kutusunda " AI Tools "**(AI Araçları)** ifadesini arayın ve istediğiniz şablonu seçin. Şablon seçerek şablonun sağladığına ilişkin kısa bir açıklama görüntülebilirsiniz.

    ![Python şablonuyla VS2017 Project yeni uygulama iletişim kutusu](media/create-project/new-ai-project.png)

3. Bu Hızlı Başlangıç için "**TensorFlow Uygulaması**" şablonunu seçin, projeye bir ad ("MNIST" gibi) ve konum girin ve Tamam'ı **seçin.**

4. Visual Studio proje dosyasını (diskte bir dosya) şablonda açıklandığı gibi `.pyproj` diğer dosyalarla birlikte oluşturur. "TensorFlow Uygulaması" şablonuyla projeniz ile aynı adlı bir dosya içerir. Dosya varsayılan olarak Visual Studio düzenleyicide açıktır.

    ![Python Uygulama şablonu kullanırken sonuçta elde edilen proje](media/create-project/new-tensorflowapp.png)

5. Kodun TensorFlow, numpy, sys ve os gibi çeşitli kitaplıkları içeri aktarmış olduğunu fark ettik. Buna ek olarak, giriş eğitim verileri, çıkış modelleri ve günlük dosyalarının konumunun kolayca değiştirilene kadar bazı giriş bağımsız değişkenleriyle hazır hale gelir. Bu params, işlerinizi birden çok işlem bağlamına (yerel geliştirme kutunuzu Azure Dosya Paylaşımından farklı bir dizin) gönderdiğinizde kullanışlıdır.

6. Projeniz ayrıca komut satırı bağımsız değişkenlerini bu giriş parametrelerine otomatik olarak aktararak uygulama hata ayıklamayı kolaylaştıracak bazı özellikler de oluşturulmuş. **Projenize sağ** tıklayın ve Özellikler'i **seçin**

    ![Özellikler'in Visual Studio Çözüm Gezgini TensorFlowApplication1 bağlam menüsünü gösteren ekran görüntüsü.](media/create-project/project-properties.png)

7. Betik **Bağımsız Değişkenleri'nin** otomatik olarak ekli olduğunu görmek için Hata Ayıkla sekmesine tıklayın. Bunları, giriş verilerinizin bulunduğu ve çıkışın depolandığı yere göre değiştirebilirsiniz.

    ![Projenin Betik Bağımsız Değişkenlerini gösteren TensorFlowApplication1 için Özellikler ayarlarında Hata Ayıklama sekmesinin ekran görüntüsü.](media/create-project//project-properties_1.png)

8. Ctrl+F5 tuşlarına basarak veya menüde Hata Ayıkla'> **Hata Ayıklama Olmadan Başlat'ı seçerek** programı çalıştırın. Sonuçlar bir konsol penceresinde görüntülenir.
