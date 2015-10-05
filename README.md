package com.publishing.model;

import java.io.Serializable;
import java.util.Date;

import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.Id;
import javax.persistence.Table;

import org.codehaus.jackson.annotate.JsonIgnoreProperties;

/**
 * An article consists of the following information: 
 * header 
 * short description
 * text 
 * publish 
 * date 
 * author(s) 
 * keyword(s)
 * 
 * @author fatalin
 * 
 */

@Entity
@Table(name = "article")
@JsonIgnoreProperties({"hibernateLazyInitializer", "handler"})
public class Article implements Serializable {

	private static final long serialVersionUID = 1L;

	@Id
	@GeneratedValue
	@Column(name = "id")
	private long id;

	@Column(name = "header")
	private String header;

	@Column(name = "text")
	/** 
	 * Max length of String is approximately 2 billion, se we're safe to hold an article in it
	 */
	private String text; 

	@Column(name = "short_description")
	private String shortDescription;

	@Column(name = "authors")
	/** 
	 * Authors will be kept in the DB as varchar (string), so we'll keep it the same
	 * in the entity class as well for simplicity. When business logic requires, it 
	 * is elementary for Java to transfer it to an iterable
	 */
	private String authors;

	@Column(name = "keywords")
	/** 
	 * Keywords will be kept in the DB as varchar (string), so we'll keep it the same
	 * in the entity class as well for simplicity. When business logic requires, it 
	 * is elementary for Java to transfer it to an iterable for example
	 */
	private String keywords;
	
	@Column(name = "publish_date")
	private Date publishDate;

	public long getId() {
		return id;
	}

	public void setId(long id) {
		this.id = id;
	}

	public String getHeader() {
		return header;
	}

	public void setHeader(String header) {
		this.header = header;
	}

	public String getText() {
		return text;
	}

	public void setText(String text) {
		this.text = text;
	}

	public String getShortDescription() {
		return shortDescription;
	}

	public void setShortDescription(String shortDescription) {
		this.shortDescription = shortDescription;
	}

	public String getAuthors() {
		return authors;
	}

	public void setAuthors(String authors) {
		this.authors = authors;
	}

	public String getKeywords() {
		return keywords;
	}

	public void setKeywords(String keywords) {
		this.keywords = keywords;
	}

	public Date getPublishDate() {
		return publishDate;
	}

	public void setPublishDate(Date publishDate) {
		this.publishDate = publishDate;
	}
}
