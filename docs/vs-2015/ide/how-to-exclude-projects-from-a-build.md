---
title: 'Nasıl yapılır: bir derlemeden projeleri hariç tutma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffa2b0fd8cab35fc73031d3ead8a5803558c2c07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667949"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Nasıl yapılır: Derlemeden Projeleri Hariç Tutma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir çözümü, içerdiği tüm projeleri oluşturmadan oluşturabilirsiniz. Örneğin, derlemeyi kesen bir projeyi dışlayabilirsiniz. Ardından, sorunları araştırıp ve adresledikten sonra projeyi derleyebilirsiniz.

 Aşağıdaki yaklaşımlardan yararlanarak bir projeyi hariç bırakabilirsiniz:

- Etkin çözüm yapılandırmasından geçici olarak kaldırılıyor.

- Projeyi içermeyen bir çözüm yapılandırması oluşturma.

  Daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../ide/understanding-build-configurations.md).

### <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Etkin çözüm yapılandırmasından bir projeyi geçici olarak kaldırmak için

1. Menü çubuğunda, **Configuration Manager** **Oluştur**' u seçin.

2. **Proje bağlamları** tablosunda, derlemeden dışlamak istediğiniz projeyi bulun.

3. Projenin **Build** sütununda, onay kutusunun işaretini kaldırın.

4. **Kapat** düğmesini seçin ve çözümü yeniden derleyin.

### <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Projeyi dışlayan bir çözüm yapılandırması oluşturmak için

1. Menü çubuğunda, **Configuration Manager** **Oluştur**' u seçin.

2. **Etkin çözüm yapılandırması** listesinde, öğesini seçin **\<New>** .

3. **Ad** kutusuna çözüm yapılandırması için bir ad girin.

4. **Ayarları Şuradan Kopyala** listesinden, yeni yapılandırmayı temel almak istediğiniz çözüm yapılandırmasını seçin (örneğin, **hata ayıklama**) ve sonra **Tamam** düğmesini seçin.

5. **Configuration Manager** iletişim kutusunda, dışlamak Istediğiniz projenin **Build** sütunundaki onay kutusunun Işaretini kaldırın ve sonra **Kapat** düğmesini seçin.

6. **Standart** araç çubuğunda, yeni çözüm yapılandırmasının **çözüm yapılandırmaları** kutusunda etkin yapılandırma olduğunu doğrulayın.

7. Menü çubuğunda **Oluştur**, **çözümü yeniden derle**öğesini seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Derleme yapılandırmasını anlama](../ide/understanding-build-configurations.md) nasıl [yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md) [nasıl yapılır: aynı anda birden fazla yapılandırma derleme](../ide/how-to-build-multiple-configurations-simultaneously.md)
