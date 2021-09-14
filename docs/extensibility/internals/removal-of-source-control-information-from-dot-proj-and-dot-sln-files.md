---
title: .proj ve .sln dosyalarından kaynak denetimi bilgilerini kaldırma
description: Kaynak Denetimi Eklentisi API'sinde SCC bilgileri msSCCPRJ içinde depolanır. Proje ve çözüm dosyaları yerine SCC dosyası.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5a6db057075b57f07a733af146915db92446a077
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725006"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>.proj ve .sln dosyalarından kaynak denetimi bilgilerini kaldırma

Kaynak Denetimi Eklentisi API'sini 1.2 sürümünde SCC bilgileri MSSCCPRJ'de depolanır. SCC dosyası. MSSCCPRJ'nin avantajı. SCC dosyası, .proj ve .sln dosyalarında olduğu gibi SCC bilgisinin kaynak denetimli olmadığını belirtir.

## <a name="version-12-changes"></a>Sürüm 1.2 Değişiklikleri

 Kaynak Denetimi Eklentisi API'si sürüm 1.1'i temel alan kaynak denetimi eklentilerde, kaynak denetimiyle ilgili bilgiler proje (.proj) ve çözüm (.sln) dosyalarında depolanır. Kaynak denetim bilgisinin veritabanı konumu AuxPath tarafından belirtilir ve veritabanındaki belirli konum ProjName tarafından belirtilir. Bu davranış dal, fork veya kopyalama işlemleri sonrasında sorunlara neden olabilir çünkü ProjName genellikle bu işlemlerden herhangi biri sonrasında geçersiz olur.

 Kaynak Denetimi Eklentisi API'si sürüm 1.1'de, IDE~ SAK dosyalarını kullanarak bir eklentinin MSSCCPRJ'yi destekleyeblip desteklemedi. Kaynak denetimi bilgilerini depolamaya ilişkin SCC yöntemi. Kaynak Denetimi Eklentisi API'si sürüm 1.2, MSSCCPRJ desteğini algılamak için yeni bir özellik sağlar. ~SAK dosyası olmadan SCC dosyası. Daha fazla bilgi için [bkz. ~SAK Dosyalarının Ortadan Kaldırılması.](../../extensibility/internals/elimination-of-tilde-sak-files.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
