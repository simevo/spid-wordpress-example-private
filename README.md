# spid-wordpress-example-private
Esempio di sito wordpress con login SPID e pagine riservate al singolo utente SPID

Dimostra come è possibile creare pagine o articoli privati riservati a specifici utenti SPID, prima che essi abbiano fatto il primo login sul sito wordpress.

## Use case

Questa funzione potrebbe essere utile:
- ad una **scuola**: per creare una pagina individuale per ogni genitore dove gli amministratori del sito inseriscono annunci / notizie riservate
- ad un'**associazione sportiva dilettantistica**: per creare degli articoli visibili solo a ciascun allenatore, relativi ad eventi sportivi o riunioni dell'associazione

## Funzionamento

Rif.: http://www.wpexpertdeveloper.com/wordpress-private-user-page-member-portal/.

### Senza plugin aggiuntivi

Si usa la soluzione 1 ("Using default WordPress pages for Private User Page") di http://www.wpexpertdeveloper.com/wordpress-private-user-page-member-portal/ aggiungendo alla pagina / all'articolo il campo custom `private_page_spid_fiscalNumber`. 

Nella pagina di configurazione del plugin [spid-wordpress](https://github.com/simevo/spid-wordpress) occorre ticcare l'attributo **Codice fiscale** (`fiscalNumber`). In questo modo quando un utente fa il login con SPID il plugin aggiunge l'attributo SPID **codice fiscale** nel database di Wordpress, nella tabella wp_usermeta, col nome `spid_fiscalNumber`.

Il codice da aggiungere al file `functions.php` deve essere modificato, facendo sì che la funzione `wcp_validate_private_page_restrictions` metta a confronto il campo custom della pagina / articolo `private_page_spid_fiscalNumber` col campo meta dell'utente `spid_fiscalNumber`.

### Con plugin WP Private Content Plus 

Installare il [plugin `wp-private-content-plus`](https://wordpress.org/plugins/wp-private-content-plus/) e utilizzare le funzioni:
- [Restrict content by multiple user meta keys](http://www.wpexpertdeveloper.com/restrict-content-by-multiple-user-meta-keys/)
- [Restrict content by multiple user meta values](http://www.wpexpertdeveloper.com/restrict-content-by-multiple-user-meta-values/)

## Demo

TODO
