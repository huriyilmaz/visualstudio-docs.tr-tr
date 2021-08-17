---
title: MSBuild C++ ' a özel görevler | Microsoft Docs
description: c++ kodu oluştururken MSBuild tarafından kullanılan c++ yüklendiğinde kullanılabilecek MSBuild görevleri bölümüne bakın.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- cplusplus
ms.openlocfilehash: 4d88d5a04126d06ad420f1af37abe3343ad23d74fd55c882f8580fd649f5e2da
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397455"
---
# <a name="msbuild-tasks-specific-to-c"></a>C++ ' a özgü MSBuild görevler

Görevler, derleme işlemi sırasında çalışan kodu sağlar. C++ yüklendiğinde, MSBuild ile yüklenenlere ek olarak aşağıdaki görevler kullanılabilir. daha fazla bilgi için bkz. [MSBuild (C++) genel bakış](/cpp/build/msbuild-visual-cpp-overview).

 Her görevin parametrelerine ek olarak, her görevin aşağıdaki parametreleri de vardır.

| Parametre | Açıklama |
|-------------------| - |
| `Condition` | İsteğe bağlı `String` parametre.<br /><br /> `Boolean`MSBuild altyapısının bu görevin yürütülüp yürütülmeyeceğini belirlemede kullandığı bir ifade. MSBuild tarafından desteklenen koşullar hakkında daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | İsteğe bağlı parametre. , Aşağıdaki değerlerden birini içerebilir:<br /><br /> -   **WarnAndContinue** veya **true**. Bir görev başarısız olduğunda, [hedef](../msbuild/target-element-msbuild.md) öğe ve yapı içindeki sonraki görevler yürütülmeye devam eder ve görevdeki tüm hatalar uyarı olarak kabul edilir<br />-   **Errportadcontinue**. Bir görev başarısız olduğunda, öğedeki sonraki görevler `Target` ve derleme yürütülmeye devam eder ve görevdeki tüm hatalar hata olarak değerlendirilir.<br />-   **Errportadstop** veya **false** (varsayılan). Bir görev başarısız olduğunda, öğe ve yapı içindeki kalan görevler `Target` yürütülmez ve tüm `Target` öğe ve derleme başarısız olarak kabul edilir.<br /><br /> 4,5 ' den önceki .NET Framework sürümleri yalnızca `true` ve değerlerini destekliyordu `false` .<br /><br /> Daha fazla bilgi için bkz. [nasıl yapılır: görevlerdeki hataları yoksayma](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[BscMake görevi](../msbuild/bscmake-task.md)|Microsoft 'A ait bilgi Bakımı yardımcı programı aracını (*bscmake.exe*) sarar.|
|[CL görevi](../msbuild/cl-task.md)|C++ derleyici aracını sarmalanmış (*cl.exe*).|
|[CPPClean görevi](../msbuild/cppclean-task.md)|bir C++ projesi yapılandırıldığında MSBuild oluşturduğu geçici dosyaları siler.|
|[ClangCompile görevi](../msbuild/clangcompile-task.md)|C++ derleyici aracını sarmalanmış (*clang.exe*).|
|[CustomBuild görevi](../msbuild/custombuild-task.md)|C++ derleyici aracını sarmalanmış (*cmd.exe*).|
|[FXC görevi](../msbuild/fxc-task.md)|Yapı sürecinde HLSL gölgelendirici derleyicileri kullanın.|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|Eski tlogs dosyalarını okur, yeni tlogs yazar ve güncel olmayan öğe kümesi döndürür. (yardımcı görev)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|Yalnızca çıkış dizini veya tam dosya adı ya da hiçbir şey belirtilmesine izin veren CL ve diğer araçların çıkış dosyası adını alır. (yardımcı görev)|
|[LIB görevi](../msbuild/lib-task.md)|Microsoft 32-bit kitaplık Yöneticisi aracını (*lib.exe*) sarmalanmış olarak kaydırır.|
|[Bağlantı görevi](../msbuild/link-task.md)|C++ bağlayıcı aracını sarmalanmış (*link.exe*).|
|[MIDL görevi](../msbuild/midl-task.md)|Microsoft Arabirim Tanımlama Dili (MıDL) derleyici aracını (*midl.exe*) sarmalanmış.|
|[MT görevi](../msbuild/mt-task.md)|Microsoft bildirim aracı 'nı (*mt.exe*) sarmalanmış.|
|[MultiToolTask görevi](../msbuild/multitooltask-task.md)|Açıklama yok.|
|[ParallelCustomBuild görevi](../msbuild/parallelcustombuild-task.md)|[CustomBuild görevinin](../msbuild/custombuild-task.md)paralel örneklerini çalıştırın.|
|[RC görevi](../msbuild/rc-task.md)|Microsoft Windows kaynak derleyicisi aracını (*rc.exe*) sarmalanmış.|
|[SetEnv görevi](../msbuild/setenv-task.md)|Belirtilen ortam değişkeninin değerini ayarlar veya siler.|
|[TrackedVCToolTask temel sınıfı](../msbuild/trackedvctooltask-base-class.md)|[Vctooltask](../msbuild/vctooltask-base-class.md)'dan devralır.|
|[VCMessage görevi](../msbuild/vcmessage-task.md)|Bir derleme sırasında uyarı iletilerini ve hata iletilerini günlüğe kaydeder. (Genişletilebilir değil. Yalnızca iç kullanım.)|
|[VCToolTask temel sınıfı](../msbuild/vctooltask-base-class.md)|[ToolTask](/dotnet/api/microsoft.build.utilities.tooltask)'dan devralır.|
|[XDCMake görevi](../msbuild/xdcmake-task.md)|XML belge açıklaması (*. xdc*) dosyalarını bir *.xml* dosyasına birleştiren XML belge aracı 'nı (*xdcmake.exe*) sarmalanmış hale gelir.|
|[XSD görevi](../msbuild/xsd-task.md)|Bir kaynaktan şema veya sınıf dosyaları üreten XML şema tanımı aracını (*xsd.exe*) sarmalanmış olarak kaydırır. *Aşağıdaki nota bakın.*|
|[MSBuild başvurusu](../msbuild/msbuild-reference.md)|MSBuild sisteminin öğelerini açıklar.|
|[Görevler](../msbuild/msbuild-tasks.md)|Bir yapı oluşturmak için birleştirilebilecek kod birimleri olan görevleri açıklar.|
|[Görev yazma](../msbuild/task-writing.md)|Bir görevin nasıl oluşturulacağını açıklar.|

> [!NOTE]
> Visual Studio 2017 ' den başlayarak *xsd.exe* için C++ proje desteği kullanım dışıdır. GAC 'ye *CppCodeProvider.dll* El Ile ekleyerek **Microsoft. VisualC. CppCodeProvider** API 'lerini kullanmaya devam edebilirsiniz.
