---
title: Şablondan bir AI projesi oluşturma
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: de0d2521f73da21ca7b6fc40edaecfadd5d703ed
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371566"
---
# <a name="create-an-ai-project-from-a-template-in-visual-studio"></a>Visual Studio 'da bir şablondan bir AI projesi oluşturma

[Visual Studio Tools for AI](installation.md)yükledikten sonra, çeşitli şablonlar kullanarak yenı bir AI projesi oluşturmak kolaydır.

1. Visual Studio’yu başlatın.

2. **Dosya > yeni > proje** ' yi seçin (Ctrl + Shift + N). **Yeni proje** iletişim kutusunda, "**AI araçları**" ifadesini arayın ve istediğiniz şablonu seçin. Şablon seçilmesi, şablonun neler sundığına ilişkin kısa bir açıklama gösterir.

    ![Python şablonuyla VS2017 yeni proje iletişim kutusu](media/create-project/new-ai-project.png)

3. Bu hızlı başlangıçta "**TensorFlow uygulaması**" şablonunu seçin, projeye bir ad verin (örneğin, "mnist") ve sonra **Tamam**' ı seçin.

4. Visual Studio, `.pyproj` şablon tarafından tanımlanan diğer dosyalarla birlikte proje dosyasını (diskte bulunan bir dosya) oluşturur. "TensorFlow uygulaması" şablonuyla proje, projenizle aynı adlı bir dosya içerir. Dosya, Visual Studio Düzenleyicisi 'nde varsayılan olarak açıktır.

    ![Python uygulama şablonu kullanılırken ortaya çıkan proje](media/create-project/new-tensorflowapp.png)

5. Kodun zaten TensorFlow, sayısal tuş takımı, sys ve OS dahil birkaç Kitaplığı İçeri aktardığına dikkat edin. Ayrıca, giriş eğitim verilerinin, çıkış modellerinin ve günlük dosyalarının konumunun geçişini kolayca sağlamak için uygulamanızı bazı giriş bağımsız değişkenleriyle hazırlayın. Bu params 'lar, işlerinizi birden çok işlem bağlamına gönderdiğinizde (yerel geliştirme kutusunda bir Azure dosya paylaşımından farklı bir dizin olan IE farklı bir dizin) yararlıdır.

6. Projenizde Ayrıca, komut satırı bağımsız değişkenlerini otomatik olarak bu giriş parametrelerine geçirerek uygulamanızda hata ayıklamayı kolaylaştırmak için bazı özellikler oluşturulmuş. Projenize sağ tıklayın ve ardından **Özellikler** **' i** seçin

    ![Özellikler](media/create-project/project-properties.png)

7. Otomatik olarak eklenen betik bağımsız değişkenlerini görmek için **Hata Ayıkla** sekmesine tıklayın. Bunları, giriş verilerinizin bulunduğu yere ve çıktının depolanacağı yere göre değiştirebilirsiniz.

    ![Özellikler](media/create-project//project-properties_1.png)

8. CTRL + F5 tuşlarına basarak veya menüden **hata ayıklama > başla** ' yı seçerek programı çalıştırın. Sonuçlar konsol penceresinde görüntülenir.
