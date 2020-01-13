---
title: UML modellerini diğer modeller ve araçlarla tümleştirin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, references to models
ms.assetid: 9e75e7d1-93cf-4196-baa3-bd10b9af16d3
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72ea0c562bb9c2a8050fc1365fac19df20232f80
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918363"
---
# <a name="integrate-uml-models-with-other-models-and-tools"></a>UML modellerini diğer modeller ve araçlarla tümleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML modelleri, diğer modellerle ve etki alanına özgü dillerle tümleştirilebilir.

 Çeşitli işlevleri gerçekleştirmek için uzantı kodu yazarak modelleri aşağıdaki yollarla tümleştirebilirsiniz:

 Herhangi bir öğeden, dosyalar gibi diğer öğelere veya diğer modellerdeki öğelere başvurular ekleyin.
UML öğesinde, diğer UML öğelerine, dosyalara veya diğer nesnelere yönelik bağlantıları dizeler olarak kodlayarak depolayabilirler.

 Örneğin, herhangi bir UML eylemini (bir etkinlik diyagramındaki bir öğe) başka bir etkinlik diyagramına bağlayabileceğiniz bir uzantı yazabilirsiniz. Kullanıcı eyleme çift tıkladığında, diğer diyagram açılır. Bu, kullanıcının eyleme daha ayrıntılı bir görünüm sağlamasına olanak sağlar.

 Dizeleri ve diğer verileri herhangi bir öğede depolayabilmeniz için iki yol vardır:

- **Stereotip özellikleri.** Belirtilen UML öğe türlerine özellikler ekleyen bir stereotipi tanımladığınız bir UML profili tanımlayabilirsiniz. Örneğin, bir UML eylemine, **detadetail** adlı bir özellik ekleyen bir profil tanımlayabilirsiniz. Bir eyleme stereotipi uygulayarak ve sonra verileri özellikte depolayarak bir eylemde bağlantı verilerini depolayan uzantı kodu yazabilirsiniz.

   Stereotip ve özellikleri Özellikler penceresi kullanıcıya görünür.

   Bu uzantıyı dağıtmak için, profil tanımını ve uzantı kodunu tek bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısında paketlemeyi caksınız.

   Daha fazla bilgi için bkz. [UML genişletmek için profil tanımlama](../modeling/define-a-profile-to-extend-uml.md).

- **Başvur.** Bir dizi dizeyi herhangi bir UML öğesine ekleyebilirsiniz. Dosya adı veya başka bir öğenin GUID 'SI gibi bilgileri depolayan bir kod yazabilirsiniz. Bu, ek tanımlar sağlanmadan yapılabilir. Başvurular Kullanıcı tarafından doğrudan görülemez.

Model öğelerine başvuruları kodlamak için iki yol vardır:

- Hedef model öğesinin **GUID ve dosya adı** ve onu içeren model veya onu görüntüleyen belirli bir diyagram.

- **ModelBus başvuruları.** ModelBus, modeller arasındaki başvuruları oluşturmak ve çözmek için bir çerçevedir. Kullanıcının modelde bir öğe seçmesini sağlayan ModelBus seçiciyi içerir. Ayrıca, hedef modeldeki değişiklikler nedeniyle kullanıcının kaybolan başvuruları çözümlemesine yardımcı olur.

   Daha fazla bilgi için bkz. [Visual Studio ModelBus kullanarak modelleri tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

  Değişiklikleri bir modelden diğerine yay.
  Örneğin, bir öğenin adını bağlantılı diyagramın adıyla eşitleyebilir, böylece Kullanıcı bir tane değiştirirse diğeri de değişir. Bunu yapmak için iki mekanizma vardır:

1. Aynı modelin içindeki değişiklikleri yaymak için **VMSDK kuralları** kullanılabilir.

2. **VMSDK Olayları** model dışındaki değişiklikleri yaymak için kullanılabilir; Örneğin, bağlantılı bir belgenin dosya adını değiştirmek veya başka bir modeldeki bir öğeyi değiştirmek için.

   Bu mekanizmalar hakkında daha fazla bilgi için bkz. [nasıl yapılır: UML modeldeki değişikliklere yanıt verme](../misc/how-to-respond-to-changes-in-a-uml-model.md).

   Öğeleri bir modelden diğerine kopyalamak için sürükleyin bir UML diyagramına öğeleri sürükleyerek kullanıcının öğe oluşturmasını sağlayabilirsiniz. Oluşturulan öğenin özgün kopyası olması gerekmez. Örneğin, kullanıcının yeni bir eylem oluşturmak için Çözüm Gezgini 'nden başka bir etkinlik diyagramına bir etkinlik diyagramı sürüklemeye izin verebilir.

   Daha fazla bilgi için bkz. [Modelleme diyagramında hareket Işleyicisi tanımlama](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) ve [nasıl yapılır: sürükle ve bırak işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [modelleme diyagramı üzerinde bir hareket işleyicisi tanımlama](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) [nasıl yapılır: sürükle ve bırak IŞLEYICISI ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md) [nasıl yapılır: UML modelindeki değişikliklere yanıt verme](../misc/how-to-respond-to-changes-in-a-uml-model.md)
