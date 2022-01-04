---
id: 1485
title: Execute Transactions from Azure Mobile App API (node.js)
date: 2016-09-21T15:19:57-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=1485
permalink: /2016/09/21/execute-transactions-from-azure-mobile-app-api-node-js/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Execute Transactions from Azure Mobile App API (node.js)" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/21/execute-transactions-from-azure-mobile-app-api-node-js/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Using the Azure Mobile App API interface (like: https://mymobileapp.azurewebsites.net/api/doTransActionStuff ) with a node.js backend, I found documentation around executing SQL Transactions a little light.  So… Here are some options you could use: 1. Call a stored procedure that does everything for you This would be the way I would do it!  Stick all of the..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Execute Transactions from Azure Mobile App API (node.js)" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/21/execute-transactions-from-azure-mobile-app-api-node-js/" />
    <meta name="twitter:description" content="Using the Azure Mobile App API interface (like: https://mymobileapp.azurewebsites.net/api/doTransActionStuff ) with a node.js backend, I found documentation around executing SQL Transactions a little light.  So… Here are some options you could use: 1. Call a stored procedure that does everything for you This would be the way I would do it!  Stick all of the..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Execute Transactions from Azure Mobile App API (node.js)" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/21/execute-transactions-from-azure-mobile-app-api-node-js/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Using the Azure Mobile App API interface (like: https://mymobileapp.azurewebsites.net/api/doTransActionStuff ) with a node.js backend, I found documentation around executing SQL Transactions a little light.  So… Here are some options you could use: 1. Call a stored procedure that does everything for you This would be the way I would do it!  Stick all of the..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Execute Transactions from Azure Mobile App API (node.js)" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/21/execute-transactions-from-azure-mobile-app-api-node-js/" />
    <meta name="twitter:description" content="Using the Azure Mobile App API interface (like: https://mymobileapp.azurewebsites.net/api/doTransActionStuff ) with a node.js backend, I found documentation around executing SQL Transactions a little light.  So… Here are some options you could use: 1. Call a stored procedure that does everything for you This would be the way I would do it!  Stick all of the..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Execute Transactions from Azure Mobile App API (node.js)" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/21/execute-transactions-from-azure-mobile-app-api-node-js/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Using the Azure Mobile App API interface (like: https://mymobileapp.azurewebsites.net/api/doTransActionStuff ) with a node.js backend, I found documentation around executing SQL Transactions a little light.  So… Here are some options you could use: 1. Call a stored procedure that does everything for you This would be the way I would do it!  Stick all of the..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Execute Transactions from Azure Mobile App API (node.js)" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/21/execute-transactions-from-azure-mobile-app-api-node-js/" />
    <meta name="twitter:description" content="Using the Azure Mobile App API interface (like: https://mymobileapp.azurewebsites.net/api/doTransActionStuff ) with a node.js backend, I found documentation around executing SQL Transactions a little light.  So… Here are some options you could use: 1. Call a stored procedure that does everything for you This would be the way I would do it!  Stick all of the..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Execute Transactions from Azure Mobile App API (node.js)" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/21/execute-transactions-from-azure-mobile-app-api-node-js/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Using the Azure Mobile App API interface (like: https://mymobileapp.azurewebsites.net/api/doTransActionStuff ) with a node.js backend, I found documentation around executing SQL Transactions a little light.  So… Here are some options you could use: 1. Call a stored procedure that does everything for you This would be the way I would do it!  Stick all of the..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Execute Transactions from Azure Mobile App API (node.js)" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/21/execute-transactions-from-azure-mobile-app-api-node-js/" />
    <meta name="twitter:description" content="Using the Azure Mobile App API interface (like: https://mymobileapp.azurewebsites.net/api/doTransActionStuff ) with a node.js backend, I found documentation around executing SQL Transactions a little light.  So… Here are some options you could use: 1. Call a stored procedure that does everything for you This would be the way I would do it!  Stick all of the..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Execute Transactions from Azure Mobile App API (node.js)" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/21/execute-transactions-from-azure-mobile-app-api-node-js/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Using the Azure Mobile App API interface (like: https://mymobileapp.azurewebsites.net/api/doTransActionStuff ) with a node.js backend, I found documentation around executing SQL Transactions a little light.  So… Here are some options you could use: 1. Call a stored procedure that does everything for you This would be the way I would do it!  Stick all of the..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Execute Transactions from Azure Mobile App API (node.js)" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/21/execute-transactions-from-azure-mobile-app-api-node-js/" />
    <meta name="twitter:description" content="Using the Azure Mobile App API interface (like: https://mymobileapp.azurewebsites.net/api/doTransActionStuff ) with a node.js backend, I found documentation around executing SQL Transactions a little light.  So… Here are some options you could use: 1. Call a stored procedure that does everything for you This would be the way I would do it!  Stick all of the..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Execute Transactions from Azure Mobile App API (node.js)" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/21/execute-transactions-from-azure-mobile-app-api-node-js/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Using the Azure Mobile App API interface (like: https://mymobileapp.azurewebsites.net/api/doTransActionStuff ) with a node.js backend, I found documentation around executing SQL Transactions a little light.  So… Here are some options you could use: 1. Call a stored procedure that does everything for you This would be the way I would do it!  Stick all of the..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Execute Transactions from Azure Mobile App API (node.js)" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/21/execute-transactions-from-azure-mobile-app-api-node-js/" />
    <meta name="twitter:description" content="Using the Azure Mobile App API interface (like: https://mymobileapp.azurewebsites.net/api/doTransActionStuff ) with a node.js backend, I found documentation around executing SQL Transactions a little light.  So… Here are some options you could use: 1. Call a stored procedure that does everything for you This would be the way I would do it!  Stick all of the..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Execute Transactions from Azure Mobile App API (node.js)" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/21/execute-transactions-from-azure-mobile-app-api-node-js/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Using the Azure Mobile App API interface (like: https://mymobileapp.azurewebsites.net/api/doTransActionStuff ) with a node.js backend, I found documentation around executing SQL Transactions a little light.  So… Here are some options you could use: 1. Call a stored procedure that does everything for you This would be the way I would do it!  Stick all of the..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Execute Transactions from Azure Mobile App API (node.js)" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/21/execute-transactions-from-azure-mobile-app-api-node-js/" />
    <meta name="twitter:description" content="Using the Azure Mobile App API interface (like: https://mymobileapp.azurewebsites.net/api/doTransActionStuff ) with a node.js backend, I found documentation around executing SQL Transactions a little light.  So… Here are some options you could use: 1. Call a stored procedure that does everything for you This would be the way I would do it!  Stick all of the..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Execute Transactions from Azure Mobile App API (node.js)" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/21/execute-transactions-from-azure-mobile-app-api-node-js/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Using the Azure Mobile App API interface (like: https://mymobileapp.azurewebsites.net/api/doTransActionStuff ) with a node.js backend, I found documentation around executing SQL Transactions a little light.  So… Here are some options you could use: 1. Call a stored procedure that does everything for you This would be the way I would do it!  Stick all of the..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Execute Transactions from Azure Mobile App API (node.js)" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2016/09/21/execute-transactions-from-azure-mobile-app-api-node-js/" />
    <meta name="twitter:description" content="Using the Azure Mobile App API interface (like: https://mymobileapp.azurewebsites.net/api/doTransActionStuff ) with a node.js backend, I found documentation around executing SQL Transactions a little light.  So… Here are some options you could use: 1. Call a stored procedure that does everything for you This would be the way I would do it!  Stick all of the..." />
    
categories:
  - Uncategorized
tags:
  - Azure Mobile Apps
---
Using the Azure Mobile App API interface (like: https://mymobileapp.azurewebsites.net/api/doTransActionStuff ) with a node.js backend, I found documentation around executing SQL Transactions a little light.  So… Here are some options you could use:

### 1. Call a stored procedure that does everything for you

This would be the way I would do it!  Stick all of the logic in a stored procedure and make the Azure SQL Database do the work for you.  This also is the best performing solution since there is only one call to the Database and the Database is doing the work for me.  This assumes you can write a stored procedure of course!  Simply call the stored procedure with arguments from within the API using something like this:

<pre class="code"><span style="color: green">// an example of executing a stored procedure that internally is using transactions
     </span><span style="color: black">post: (request, response, next) =&gt; {
             </span><span style="color: blue">var </span><span style="color: black">query = {
                     sql: </span><span style="color: #a31515">'EXEC completeAllStoredProcedure @completed'</span><span style="color: black">,
                 parameters: [
                     { name: </span><span style="color: #a31515">'completed'</span><span style="color: black">, value: request.query.completed }
             ]
         };
         request.azureMobile.data.execute(query)
             .then(</span><span style="color: blue">function </span><span style="color: black">(results) {
                     response.json(results);
                 });
     }
</span></pre>

Sample: <a target="_blank" href="https://github.com/Azure/azure-mobile-apps-node/blob/master/samples/custom-api-sql-stmt/api/completeall.js" title="https://github.com/Azure/azure-mobile-apps-node/blob/master/samples/custom-api-sql-stmt/api/completeall.js">https://github.com/Azure/azure-mobile-apps-node/blob/master/samples/custom-api-sql-stmt/api/completeall.js</a>  
Note: The parameters are passed in via the client.  The raw HTTP would look something like this –> <http://mymobileapp.azurewebsites.net/api/doTransActionStuff?completed=true>.  For .NET Clients you would use InvokeApiAsync <a target="_blank" href="https://msdn.microsoft.com/en-us/library/azure/dn268343(v=azure.10).aspx" title="https://msdn.microsoft.com/en-us/library/azure/dn268343(v=azure.10).aspx">https://msdn.microsoft.com/en-us/library/azure/dn268343(v=azure.10).aspx</a>  
iOS clients: InvokeApi <a target="_blank" href="https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-ios-how-to-use-client-library/" title="https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-ios-how-to-use-client-library/">https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-ios-how-to-use-client-library/</a>  
&nbsp;

### 2. Call execute and build your statements into a query

Yet another way that would be fairly efficient is to build up the SQL statement as a string and embedded any passed in parameters (like above) if necessary and call execute

<pre class="code"><span style="color: #a31515">"get"</span><span style="color: black">: </span><span style="color: blue">function </span><span style="color: black">(req, res, next) {
    </span><span style="color: blue">var </span><span style="color: black">query = {
        sql: </span><span style="color: #a31515">"SET XACT_ABORT ON \
                    BEGIN TRANSACTION \
                    &lt;”normal” statement that works&gt; \
                    &lt;”invalid” statement that goes against a constraint I created&gt; \
                    COMMIT TRANSACTION \
                    SET XACT_ABORT OFF"</span><span style="color: black">,
        parameters: []
    };
    req.azureMobile.data.execute(query);
}</span></pre>

&nbsp;

### 3. User the built in Driver Transaction functionality

I would use this if I am already familiar with driver (like tedious) and want all my code to be in the Mobile App.  Not the most efficient and results in several calls to the Database:

<pre class="code"><span style="color: black">module.exports = {
    </span><span style="color: #a31515">"get"</span><span style="color: black">: </span><span style="color: blue">function </span><span style="color: black">(req, res, next) {
        </span><span style="color: blue">var </span><span style="color: black">globalErrMessage = </span><span style="color: #a31515">""</span><span style="color: black">;
        </span><span style="color: blue">function </span><span style="color: black">handleErr(source, err) {
            </span><span style="color: blue">var </span><span style="color: black">theError = source + </span><span style="color: #a31515">": " </span><span style="color: black">+ err;
            console.error(theError);
            globalErrMessage = globalErrMessage + theError;
            globalSuccess = </span><span style="color: blue">false</span><span style="color: black">;
        }
        </span><span style="color: blue">var </span><span style="color: black">sql = require(</span><span style="color: #a31515">'mssql'</span><span style="color: black">);
        </span><span style="color: blue">var </span><span style="color: black">config = {
            driver: </span><span style="color: #a31515">'tedious'</span><span style="color: black">, </span><span style="color: green">// use tedious driver
            </span><span style="color: black">server: </span><span style="color: #a31515">'jsandersmobileappdbserver.database.windows.net'</span><span style="color: black">,
            user: </span><span style="color: #a31515">'username@jsandersmobileappdbserver'</span><span style="color: black">,
            password: </span><span style="color: #a31515">'password'</span><span style="color: black">,
            port: </span><span style="color: #a31515">'1433'</span><span style="color: black">,
            options: {
                encrypt: </span><span style="color: blue">true</span><span style="color: black">,
                database: </span><span style="color: #a31515">'jsandersmobileDb'</span><span style="color: black">,
                debug: {
                    packet: </span><span style="color: blue">true</span><span style="color: black">,
                    data: </span><span style="color: blue">true</span><span style="color: black">,
                    payload: </span><span style="color: blue">true</span><span style="color: black">,
                    token: </span><span style="color: blue">false</span><span style="color: black">,
                    log: </span><span style="color: blue">true
                </span><span style="color: black">}
            }
        };
        </span><span style="color: blue">var </span><span style="color: black">rolledBack = </span><span style="color: blue">false</span><span style="color: black">;
        </span><span style="color: blue">var </span><span style="color: black">globalSuccess = </span><span style="color: blue">true</span><span style="color: black">;
        console.info(</span><span style="color: #a31515">"starting"</span><span style="color: black">);
        sql.connect(config, </span><span style="color: blue">function </span><span style="color: black">(err) {
            </span><span style="color: blue">if </span><span style="color: black">(err) {
                handleErr(</span><span style="color: #a31515">"sql.connect"</span><span style="color: black">, err);
            }
            </span><span style="color: blue">else </span><span style="color: black">{
                </span><span style="color: green">// ... error checks - todo
                </span><span style="color: black">console.info(</span><span style="color: #a31515">"OK:connected"</span><span style="color: black">);
                </span><span style="color: blue">var </span><span style="color: black">transaction = </span><span style="color: blue">new </span><span style="color: black">sql.Transaction(</span><span style="color: green">/* [connection] */</span><span style="color: black">);
                transaction.begin(</span><span style="color: blue">function </span><span style="color: black">(err) {
                    </span><span style="color: green">// ... error checks
                    </span><span style="color: blue">if </span><span style="color: black">(err) {
                        handleErr(</span><span style="color: #a31515">"transaction.begin"</span><span style="color: black">, err);
                    }
                    </span><span style="color: green">//Rollback event
                    </span><span style="color: black">transaction.on(</span><span style="color: #a31515">'rollback'</span><span style="color: black">, </span><span style="color: blue">function </span><span style="color: black">(aborted) {
                        </span><span style="color: green">// emited with aborted === true
                        </span><span style="color: black">console.info(</span><span style="color: #a31515">"Event:transaction.on('rollback')"</span><span style="color: black">);
                        rolledBack = </span><span style="color: blue">true</span><span style="color: black">;
                    });
                    </span><span style="color: blue">var </span><span style="color: black">request = </span><span style="color: blue">new </span><span style="color: black">sql.Request(transaction);
                    request.query(</span><span style="color: #a31515">'insert into mytable (bitcolumn) values (2)'</span><span style="color: black">, </span><span style="color: blue">function </span><span style="color: black">(err, recordset) {
                        </span><span style="color: green">// insert should fail because of invalid value
                        </span><span style="color: blue">if </span><span style="color: black">(err) {
                            handleErr(</span><span style="color: #a31515">"ERR:request.query"</span><span style="color: black">, err);
                            </span><span style="color: green">// if not rolled back then rollback this transaction
                            </span><span style="color: blue">if </span><span style="color: black">(!rolledBack) {
                                transaction.rollback(</span><span style="color: blue">function </span><span style="color: black">(err) {
                                    </span><span style="color: blue">if </span><span style="color: black">(err) {
                                        handleErr(</span><span style="color: #a31515">"ERR:transaction.rollback"</span><span style="color: black">, err);
                                    }
                                    </span><span style="color: blue">else </span><span style="color: black">{
                                        console.info(</span><span style="color: #a31515">"OK:transaction.rollback"</span><span style="color: black">);
                                    }
                                });
                            }
                        } </span><span style="color: blue">else </span><span style="color: black">{
                            transaction.commit(</span><span style="color: blue">function </span><span style="color: black">(err) {
                                </span><span style="color: green">// ... error checks
                                </span><span style="color: blue">if </span><span style="color: black">(err) {
                                    console.log(</span><span style="color: #a31515">"ERR:transaction.commit"</span><span style="color: black">);
                                    console.log(err);
                                }
                                </span><span style="color: blue">else </span><span style="color: black">{
                                    console.log(</span><span style="color: #a31515">"OK:transaction.commit"</span><span style="color: black">);
                                }
                            });
                        }
                    });
                });
            }
        });
        </span><span style="color: blue">if </span><span style="color: black">(rolledBack) {
            res.json(</span><span style="color: #a31515">"Rolled Back"</span><span style="color: black">);
        }
        </span><span style="color: blue">else if </span><span style="color: black">(globalSuccess) {
            res.json(</span><span style="color: #a31515">"success"</span><span style="color: black">);
        }
        </span><span style="color: blue">else </span><span style="color: black">{
            res.json(</span><span style="color: #a31515">"error"</span><span style="color: black">);
        }
    }
};
</span></pre>

&nbsp;  
I hope this is useful in getting you jumpstarted!  
Drop me a note if you find this useful!