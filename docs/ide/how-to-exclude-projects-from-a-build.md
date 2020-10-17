---
title: 'Nasıl yapılır: bir derlemeden projeleri hariç tutma'
description: Visual Studio 'Yu, içerdiği tüm projeleri oluşturmadan bir çözüm oluşturmak için nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b0e164c24770048495d16da852523b3dd50a43a
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136907"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Nasıl yapılır: bir derlemeden projeleri hariç tutma

Bir çözümü, içerdiği tüm projeleri oluşturmadan oluşturabilirsiniz. Örneğin, derlemeyi kesen bir projeyi dışlayabilirsiniz. Ardından, sorunları araştırıp ve adresledikten sonra projeyi derleyebilirsiniz.

Aşağıdaki yaklaşımlardan yararlanarak bir projeyi hariç bırakabilirsiniz:

- Etkin çözüm yapılandırmasından geçici olarak kaldırılıyor.

- Projeyi içermeyen bir çözüm yapılandırması oluşturma.

Daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../ide/understanding-build-configurations.md).

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Etkin çözüm yapılandırmasından bir projeyi geçici olarak kaldırmak için

1. Menü çubuğunda Configuration Manager **Oluştur**' u seçin  >  **Configuration Manager**.

2. **Proje bağlamları** tablosunda, derlemeden dışlamak istediğiniz projeyi bulun.

3. Projenin **Build** sütununda, onay kutusunun işaretini kaldırın.

4. **Kapat** düğmesini seçin ve çözümü yeniden derleyin.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Projeyi dışlayan bir çözüm yapılandırması oluşturmak için

1. Menü çubuğunda Configuration Manager **Oluştur**' u seçin  >  **Configuration Manager**.

2. **Etkin çözüm yapılandırması** listesinde, öğesini seçin **\<New>** .

3. **Ad** kutusuna çözüm yapılandırması için bir ad girin.

4. **Ayarları Şuradan Kopyala** listesinden, yeni yapılandırmayı temel almak istediğiniz çözüm yapılandırmasını seçin (örneğin, **hata ayıklama**) ve sonra **Tamam** düğmesini seçin.

5. **Configuration Manager** iletişim kutusunda, dışlamak Istediğiniz projenin **Build** sütunundaki onay kutusunun Işaretini kaldırın ve sonra **Kapat** düğmesini seçin.

6. **Standart** araç çubuğunda, yeni çözüm yapılandırmasının **çözüm yapılandırmaları** kutusunda etkin yapılandırma olduğunu doğrulayın.

7. Menü çubuğunda **derleme**  >  **yeniden oluşturma çözümü**' ni seçin.

## <a name="skipped-projects"></a>Atlanan projeler

Projeler, güncel olmadıkları veya yapılandırmadan dışlandığı için derleme sırasında atlanabilir. Visual Studio, projelerinizi derlemek için MSBuild kullanır. MSBuild, dosya zaman damgalarına göre belirlendiği şekilde yalnızca çıkış girdiden eskiyse bir hedef oluşturur. Yeniden derlemeyi zorlamak için, **derleme**  >  **yeniden oluşturma çözümünü**kullanın.

**Çıkış** penceresinin **derleme** bölmesinde, Visual Studio güncel olan proje sayısını, başarıyla oluşturulan sayıyı, başarısız olan sayıyı ve atlanan sayıyı raporlar. Atlanan sayı, güncel olduklarından derlenmediği projeleri içermiyor. Projeler etkin yapılandırmadan dışlandıklarında, derleme sırasında atlanır. Yapı çıkışında, projenin atlandığını belirten bir ileti görürsünüz:

```output
2>------ Skipped Build: Project: ConsoleApp2, Configuration: Debug x86 ------
2>Project not selected to build for this solution configuration
```

Projenin neden atlandığını öğrenmek için etkin yapılandırmayı ( `Debug x86` Önceki örnekte) ve **derleme**  >  **Configuration Manager**' yı seçin. Bu makalede anlatıldığı gibi her yapılandırma için hangi projelerin atlandığını görüntüleyebilir veya değiştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md)
- [Nasıl yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md)
- [Nasıl yapılır: aynı anda birden fazla yapılandırma derleme](../ide/how-to-build-multiple-configurations-simultaneously.md)
