RESULTADOS DE VERIFICACAO FORMAL - MonoxGuard-RT (PGENE601)
===========================================================

Ferramentas: ESBMC 8.2.0 (solver Z3 4.8.12) e CBMC 5.95.1 (solver MiniSAT 2.2.1)

ARQUIVOS:
  1_calib_*       - conversao ADC->ppm sempre em [0, PPM_MAX]        (SUCCESSFUL)
  2_detection_*   - estado valido + vivacidade (3x>=800ppm => ALARM) (SUCCESSFUL)
  3_filter_*      - invariantes da janela circular (N=8)             (SUCCESSFUL)
  4_calib_BUG_*   - versao ingenua 32 bits (experimento de falha)    (FAILED: overflow)
  RESUMO.txt      - quadro geral dos 8 resultados

Cada arquivo contem a saida completa da ferramenta, incluindo o contraexemplo
de overflow no caso do experimento de injecao de falha (harness_calib_bug).

Comandos usados (exemplos):
  esbmc harness_calib.c ../src/core/calib.c -I . -I ../src/core --overflow-check
  cbmc  harness_calib.c ../src/core/calib.c -I . -I ../src/core --signed-overflow-check --bounds-check --div-by-zero-check
