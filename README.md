algoritmo censo_demografico;
// Síntese
//  Objetivo: Traçar um perfil demográfico de um número n de entrevistados;
//  Entrada : idade, renda média e sexo de um conjunto n de pessoas;
//  Saída   : idade média, renda média e proporção entre homens e mulheres;


principal
	// Declarações
	real renda, rendas[1000], rendimento_medio, media_das_idades, prop_homem, prop_mulher, renda_maior;
	inteiro n, i, j, qtd_homem, qtd_mulher, idade, idades[1000], idade_maior;
	texto nome, nomes[1000], sexo, sexos[1000], nome_maioridade, nome_maiorenda;
	
	// Instruções
	escreva ("Digite a quantidade de participantes: ");
	leia (n);
	escreval ("");

	//Construção do vetor;
	para (i de 0 ate n - 1 passo 1) faca
		escreva ("Digite o nome: ");
		leia (nome);
		nomes[i] = nome;
		escreva ("Digite a renda mensal: ");
		leia (renda);
		rendas[i] = renda;
		escreva ("Digite a idade: ");
		leia (idade);
		idades[i] = idade;
		escreva ("Digite h ou H se homem e m ou M se mulher: ");
		leia (sexo);
		escreval ("");
		sexos[i] = sexo;
	fimPara	

	//Saber a proporção entre homens e mulheres
	qtd_homem = 0;
	qtd_mulher = 0;
	para (i de 0 ate n - 1 passo 1) faca
		se ((comparaTexto (sexos[i], "h") == 0) ou (comparaTexto (sexos[i], "H") == 0)) entao
			qtd_homem = qtd_homem + 1;
		fimSe
	fimPara		
	
	para (i de 0 ate n - 1 passo 1) faca
		se ((comparaTexto (sexos[i], "M") == 0) ou (comparaTexto (sexos[i], "m") == 0)) entao
			qtd_mulher = qtd_mulher + 1;
		fimSe
	fimPara	
	
	//Calcular a idade média e a renda média dos participantes
	rendimento_medio = renda_media (n, rendas);
	media_das_idades = idade_media (n, idades);
	prop_homem = (qtd_homem/n) * 100;
	prop_mulher = (qtd_mulher/n) * 100;
	escreval ("PERFIL DEMOGRÁFICO");
	escreval ("Renda Média = ", rendimento_medio::2);
	escreval ("Idade média = ", media_das_idades::2);
	escreval ("Proporção de homens = ", prop_homem::2, " %");
	escreval ("Proporção de mulheres = ", prop_mulher::2, " %");

	//Ordenar em ordem decrescente a idade e a renda dos participantes;
	nome_maioridade = nomes[0];
	nome_maiorenda = nomes[0];
	idade_maior = 0;
	renda_maior = 0;
	escreval ("Ranking de idades");
	para (i de 0 ate n - 1 passo 1) faca
		para (j de i ate n - 1 passo 1) faca
			se (idades[j] > idades[i]) entao
				nome_maioridade = nomes[j];
				nomes[j] = nomes[i];
				nomes[i] = nome_maioridade;
				idade_maior = idades[j];
				idades[j] = idades[i];
				idades[i] = idade_maior;
			fimSe
		fimPara
		escreval (i + 1, " - ", nomes[i]);
	fimPara		

	escreval ("Ranking de rendas");
	para (i de 0 ate n - 1 passo 1) faca
		para (j de i ate n - 1 passo 1) faca
			se (rendas[j] > rendas[i]) entao
				nome_maiorenda = nomes[j];
				nomes[j] = nomes[i];
				nomes[i] = nome_maiorenda;
				renda_maior = rendas[j];
				rendas[j] = rendas[i];
				rendas[i] = renda_maior;
			fimSe
		fimPara
		escreval (i + 1, " - ", nomes[i]);
	fimPara		

fimPrincipal

//Construção de funções para o cálculo da renda média e da idade média dos participantes;
funcao real renda_media (inteiro n, real rendas[])
	inteiro i;
	real soma, rendimento_medio;
	soma = 0;
	para (i de 0 ate n - 1 passo 1) faca
		soma = soma + rendas[i];
	fimPara
	rendimento_medio = soma/n;
	retorna rendimento_medio;
fimFuncao

funcao real idade_media (inteiro n, inteiro idades[])
	inteiro i;
	real soma, media_das_idades;
	soma = 0;
	para (i de 0 ate n - 1 passo 1) faca
		soma = soma + idades[i];
	fimPara
	media_das_idades = soma/n;
	retorna media_das_idades;
fimFuncao		
