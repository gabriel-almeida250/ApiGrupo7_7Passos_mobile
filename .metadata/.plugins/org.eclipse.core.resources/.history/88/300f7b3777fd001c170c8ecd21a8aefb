package com.residencia.comercio.repositories;

import java.math.BigDecimal;
import java.util.List;

import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;
import org.springframework.data.repository.query.Param;

import com.residencia.comercio.dtos.ProdutoInterfaceDTO;
import com.residencia.comercio.entities.Produto;

public interface ProdutoRepository extends JpaRepository<Produto, Integer> {
	@Query(value="Select "
			+ " id_produto AS idProduto,"
			+ " sku,"
			+ " nome_produto AS nomeProduto,"
			+ " descricao_produto AS descricaoProduto,"
			+ " imagem_produto AS imagemProduto,"
			+ " preco_produto AS precoProduto,"
			+ " (Select f.razao_social From fornecedor f Where f.id_fornecedor = p.id_fornecedor) AS nomeFornecedor,"
			+ " id_fornecedor AS idFornecedor,"
			+ " (Select c.nome_categoria From categoria c Where c.id_categoria = p.id_categoria) AS nomeCategoria,"
			+ " id_categoria AS idCategoria"
			+ " From produto p"
			+ " Where"
			+ " ("
			+ "	lower(p.nome_produto) like lower(concat('%', :keyword, '%'))"
			+ "	or lower(p.descricao_produto) like lower(concat('%', :keyword, '%'))"
			+ " )"
			, nativeQuery = true)
	List<ProdutoInterfaceDTO> busca(@Param("keyword") String keyword);
}
