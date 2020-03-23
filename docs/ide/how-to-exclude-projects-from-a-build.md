---
title: 'Nasıl yapılsın: Projeleri yapıdan hariç tutma'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a19c49482c45aa0a3cf5d7cb33eb106adb65b83b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114807"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Nasıl yapılsın: Projeleri yapıdan hariç tutma

İçerdiği tüm projeleri oluşturmadan bir çözüm oluşturabilirsiniz. Örneğin, yapıyı bozan bir projeyi hariç tutabilirsiniz. Daha sonra, sorunları araştırdıktan ve ele aldıktan sonra projeyi oluşturabilirsiniz.

Aşağıdaki yaklaşımları alarak bir projeyi hariç tutabilirsiniz:

- Etkin çözüm yapılandırmasından geçici olarak kaldırma.

- Projeyi içermeyen bir çözüm yapılandırması oluşturma.

Daha fazla bilgi için yapı [yapılandırmalarını anlayın.](../ide/understanding-build-configurations.md)

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Bir projeyi etkin çözüm yapılandırmasından geçici olarak kaldırmak için

1. Menü çubuğunda**Yapı Yapılandırma Yöneticisi'ni** **seçin.** > 

2. Proje **bağlamları** tablosunda, oluşturmaktan hariç tutmak istediğiniz projeyi bulun.

3. Proje için **Yapı** sütununda onay kutusunu temizleyin.

4. **Kapat** düğmesini seçin ve ardından çözümü yeniden oluşturun.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Projeyi dışlayan bir çözüm yapılandırması oluşturmak için

1. Menü çubuğunda**Yapı Yapılandırma Yöneticisi'ni** **seçin.** > 

2. Etkin **çözüm yapılandırma** listesinde ** \<Yeni>'yi **seçin.

3. **Ad** kutusuna, çözüm yapılandırması için bir ad girin.

4. Listeden **Kopya ayarlarında,** yeni yapılandırmayı (örneğin **Hata Ayıklama)** temel almak istediğiniz çözüm yapılandırmasını seçin ve ardından **Tamam** düğmesini seçin.

5. Configuration **Manager** iletişim kutusunda, hariç tutmak istediğiniz proje için **Yapı** sütunundaki onay kutusunu temizleyin ve ardından **Kapat** düğmesini seçin.

6. **Standart** araç çubuğunda, yeni çözüm yapılandırmasının **Çözüm Yapılandırmaları** kutusundaki etkin yapılandırma olduğunu doğrulayın.

7. Menü çubuğunda, **Çözüm** > **Oluştur'u**seçin.

## <a name="skipped-projects"></a>Atlanan projeler

Projeler, güncel olmadıkları veya yapılandırmanın dışında tutuldukları için yapı sırasında atlanabilir. Visual Studio, projelerinizi oluşturmak için MSBuild'i kullanır. MSBuild yalnızca dosya zaman damgaları tarafından belirlendiği gibi, çıktı girişten daha eskiyse bir hedef oluşturur. Yeniden oluşturmayı zorlamak **için, Rebuild** > **Solution**komutunu kullanın.

**Çıktı** penceresinin **Yapı** bölmesinde Visual Studio, güncel olan proje sayısını, başarıyla oluşturulmuş olan sayısını, başarısız olan sayıyı ve atlanan sayıyı bildirir. Atlanan sayım, güncel oldukları için oluşturulmayan projeleri içermez. Projeler etkin yapılandırmanın dışında kaldığında, yapı sırasında atlanır. Yapı çıktısında, projenin atlalı olduğunu belirten bir ileti görürsünüz:

```output
2>------ Skipped Build: Project: ConsoleApp2, Configuration: Debug x86 ------
2>Project not selected to build for this solution configuration
```

Projenin neden atlandığını öğrenmek için etkin yapılandırmayı`Debug x86` (önceki örnekte) not edin ve **Yapı** > **Yapılandırma Yöneticisi'ni**seçin. Bu makalede belirtildiği gibi, her yapılandırma için hangi projelerin atlandığı görüntüleyebilir veya değiştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md)
- [Nasıl yapılı: Yapılandırmalar oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md)
- [Nasıl yapılı: Aynı anda birden çok yapılandırma oluşturma](../ide/how-to-build-multiple-configurations-simultaneously.md)
