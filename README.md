

-- 1. Quantas vezes Natalie Portman foi indicada ao Oscar?
SELECT COUNT(*) 
FROM indicados_ao_oscar 
WHERE nome_do_indicado  = "Natalie Portman";
-- Resposta: 3.

-- 2. Quantos Oscars Natalie Portman ganhou? 
SELECT COUNT(*) 
FROM indicados_ao_oscar 
WHERE nome_do_indicado = "Natalie Portman" 
AND vencedor  = "sim";
-- Resposta: 1.

-- 3. Amy Adams ja ganhou algum Oscar?
SELECT COUNT(*) 
FROM indicados_ao_oscar 
WHERE nome_do_indicado = "Amy Adams" 
AND vencedor = "sim";
-- Resposta: Não, mas concorreu 6 vezes.

-- 4. A série de filmes Toy Story ganhou um Oscar em quais anos?
SELECT *
FROM indicados_ao_oscar
WHERE nome_do_filme = "Toy Story";
-- Resposta: Toy Story não ganhou nenhum oscar.

-- 5. A partir de que ano que a categoria "Actress" deixa de existir?
SELECT MAX(ano_cerimonia)
FROM indicados_ao_oscar 
WHERE categoria = "Actress";
-- Resposta: A categoria deixou de existe no ano de 1977.

-- 6. O primeiro Oscar para melhor Atriz foi para quem? Em que ano?
SELECT nome_do_indicado, ano_cerimonia
FROM indicados_ao_oscar 
WHERE categoria = "Actress" 
ORDER BY ano_cerimonia
LIMIT 1;
-- O primeiro Oscar de melhor Atriz foi para Louise Dresser no ano de 1928.


-- 7. Na coluna/campo "Vencedor", altere todos os valores com "Sim" para 1 e todos os valores "Não" para 0.
UPDATE indicados_ao_oscar
SET vencedor = CASE 
                    WHEN vencedor = "Sim" THEN 1
                    WHEN vencedor = "Não" THEN 0
                    ELSE vencedor
END;
-- Resposta: Alteração realizada.

-- 8.  Em qual edição do Oscar "Crash" concorreu ao Oscar?
SELECT ano_cerimonia
FROM indicados_ao_oscar 
WHERE nome_do_filme = "Crash";
-- Resposta: "Crash" concorreu ao Oscar no ano de 2006.

-- 9. Bom... dê um Oscar para um filme que merece muito, mas não ganhou.
SELECT (*)
FROM indicados_ao_oscar 
WHERE nome_do_filmes =  "Cidade de Deus";

-- 10. O filme Central do Brasil aparece no Oscar?
SELECT *
FROM indicados_ao_oscar
WHERE nome_do_filme = "Central do Brasil";
-- Resposta: O filme Central do Brasil não aparece no Oscar.

-- 11.Inclua no banco 3 filmes que nunca foram nem nomeados ao Oscar, mas que merecem ser. 
INSERT INTO filmes (ano_filmagem, ano_cerimonia, edicao_cerimonia, categoria, nome_do_indicado, nome_filme, vencedor)
VALUES ('2002', 2003, 75, 'BEST PICTURE', 'Cidade de Deus', 'Cidade de Deus', 'Sim');

-- 12. Pensando no ano em que você nasceu: Qual foi o Oscar de melhor filme, Melhor Atriz e Melhor Diretor?
SELECT nome_do_filme, nome_do_indicado, categoria
FROM indicados_ao_oscar
WHERE ano_cerimonia = 2005
AND categoria IN ('BEST PICTURE', 'ACTRESS IN A LEADING ROLE', 'DIRECTING');


