# Tool Directory

This directory lists the AI tools that are defined in vork-prototype.

You can open any tool page to see what it does, which input fields it accepts, and whether it is hidden or restricted.

## Static tool definitions by category

Badge legend used on individual tool pages:

- `Default Tool`: The tool is included by default for at least one built-in agent (for example, Surface Developer or other system-provided agents).
- `Restricted`: The tool requires explicit authorization/approval before it can be executed.

### Agent Orchestration

| Tool | Description | Full page |
|---|---|---|
| listAgentTemplates | List all configured agent templates. Returns each template's UUID, name, system prompt, and the list of allowed tool bean IDs. | [listAgentTemplates](list-agent-templates.md) |
| listAvailableTools | List all registered tool callbacks with their IDs and descriptions. Use this to discover valid tool IDs when building or reviewing an AgentTemplate's allowedTools list. | [listAvailableTools](list-available-tools.md) |
| readChatHistory | Read one chat-history item's full content from the current session only. Supports references: message UUID, 'uuid:<uuid>', numeric index, 'index:<n>', '-1' for last item, 'last', and 'last-assistant'. | [readChatHistory](read-chat-history.md) |
| completeBackgroundTask | Signals that the background task has entirely fulfilled its operational objectives and that the background processing loop should now gracefully terminate. You MUST supply a boolean 'success' value and a 'report' string summarising what was done and produced. | [completeBackgroundTask](complete-background-task.md) |
| delegateTask | Delegate work to another agent using a dynamic one-off background run. If jobUuid is provided, its policy/tooling settings are inherited and validated against the selected agent; if omitted, the run is created directly from the target background agent plus the provided prompt. | [delegateTask](delegate-task.md) |
| completeSkillExecution | Signals that the skill has fully completed its objective. Call this exactly once with the skill output when all required work is done. | [completeSkillExecution](complete-skill-execution.md) |

### Attention

| Tool | Description | Full page |
|---|---|---|
| createAttentionAlert | Create an attention alert for one or more channels. Channel names are globally unique and case-insensitive. Resolution policy must be ACTION_REQUIRED or DISMISSABLE. Prefer DISMISSABLE when there is no actionUrl, and use ACTION_REQUIRED when actionUrl is present. Never use FIRST_ACK or ALL_ACK. If a channel query is ambiguous, this tool suspends and asks the user to choose the intended channel. | [createAttentionAlert](create-attention-alert.md) |
| requestInformation | Request information from one or more channels by generating per-recipient input links, creating attention alerts, and optionally sending out-of-band notifications. requesterMessage and recipientMessage are required and must be explicitly authored for each call. Response policy can be AUTO, FIRST, ALL, or QUORUM. The tool suspends the current session until the response threshold is met. | [requestInformation](request-information.md) |

### Authorization

| Tool | Description | Full page |
|---|---|---|
| requestAuthorization | Create a pre-authorization token for an exact restricted tool payload. This tool is itself restricted and requires explicit approval. Tokens are one-time and consumed only when the target restricted tool is called with an exact payload match. | [requestAuthorization](request-authorization.md) |
| configureSessionApproval | Configure or clear a session-scoped approval override for protected tool calls. Admin-only: requires USERS_MANAGE. Use clear=true to remove override. When enabled, provide either policyId, policyName, or channelNames. responsePolicy supports FIRST, ALL, or QUORUM. | [configureSessionApproval](configure-session-approval.md) |

### Command Execution

| Tool | Description | Full page |
|---|---|---|
| executeCommandAndOutputTool | Executes a synchronous shell command, waits for it to complete, and returns the full output. | [executeCommandAndOutputTool](execute-command-and-output-tool.md) |
| startProcessTool | Starts a long-running background process and returns a reference PID to interact with it later. | [startProcessTool](start-process-tool.md) |
| readProcessTool | Reads and drains available unread output from a background process. | [readProcessTool](read-process-tool.md) |
| writeProcessTool | Writes input text to the stdin of a running background process. | [writeProcessTool](write-process-tool.md) |
| stopProcessTool | Terminates a background process and cleans up its memory footprint. | [stopProcessTool](stop-process-tool.md) |
| checkProcessTool | Checks if a background process is still running. | [checkProcessTool](check-process-tool.md) |

### Command Dependencies
| Tool | Description | Full page |
|---|---|---|
| resolveArchitecture | Detect the runtime architecture for the current execution environment. No arguments required. | [resolveArchitecture](resolve-architecture.md) |
| installCommand | Register a command binary directory under the session tools environment so local process execution can resolve it via PATH. | [installCommand](install-command.md) |
| isCommandInstalled | Check whether a command is available in registered session command paths. | [isCommandInstalled](is-command-installed.md) |


### Diagnostics

| Tool | Description | Full page |
|---|---|---|
| logInfo | Write a message to the application log at INFO level for tracking and diagnostics. | [logInfo](log-info.md) |

### Encoding & Crypto

| Tool | Description | Full page |
|---|---|---|
| base64DecodeString | Decode Base64 text to a UTF-8 string. | [base64DecodeString](base64-decode-string.md) |
| base64EncodeString | Encode a UTF-8 string as Base64 text. | [base64EncodeString](base64-encode-string.md) |
| configureEncryption | Configure session encryption mode for encryptString/decryptString. Use type=RSA with a PKCS#8 private key file, or type=SOFTWARE with a .p12 keystore file. For SOFTWARE, keystoreAlias and keystorePassword are optional and defaults are used when omitted. Use clear=true to revert to system default encryption. | [configureEncryption](configure-encryption.md) |
| decryptString | Decrypt text using session encryption config if present; otherwise system default encryption is used. | [decryptString](decrypt-string.md) |
| encryptString | Encrypt a UTF-8 string using session encryption config if present; otherwise system default encryption is used. | [encryptString](encrypt-string.md) |
| generatePrivateKey | Generate an RSA or Ed25519 key pair, store the private key securely, and return safe references for later signing and verification. | [generatePrivateKey](generate-private-key.md) |
| getPublicKey | Return the Base64-encoded X.509 public key bytes for a key identifier created by generatePrivateKey. Use the same secretName/reference used for signing. | [getPublicKey](get-public-key.md) |
| signData | Sign UTF-8 string data using a private key and algorithm (for example SHA256withRSA). Returns Base64 signature text. privateKey should normally be provided as a secret reference such as {{signing.key.main}} from generatePrivateKey.privateKeySecretRef. Supported signature algorithms include SHA256withRSA and Ed25519. | [signData](sign-data.md) |
| verifyData | Verify UTF-8 string data against a Base64 signature and public key using the provided algorithm. Returns true or false. | [verifyData](verify-data.md) |
| verifyDataByRef | Verify UTF-8 string data against a Base64 signature using the public key looked up by key identifier from generatePrivateKey. Pass secretName as either the plain key name or {{secretName}} reference. Supports SHA256withRSA and Ed25519. | [verifyDataByRef](verify-data-by-ref.md) |

### File Utilties

| Tool | Description | Full page |
|---|---|---|
| createPdf | Create a PDF file from MARKDOWN (default) or HTML content, store it in the session/shared file area, and return a direct download URL. Set attachToChat=false to generate the PDF without adding a chat attachment. Response guidance: do not paste raw download URLs in assistant text; generated files are auto-attached to the chat message. | [createPdf](create-pdf.md) |
| createSessionTextFile | Create a UTF-8 text file in either the per-session sandbox (default) or the shared area. Returns a download URL that can be rendered in chat attachments. Use area=SESSION for files scoped to the current chat session, or area=SHARED for cross-session exchange. Response guidance: do not paste raw download URLs in assistant text; generated files are auto-attached to the chat message. | [createSessionTextFile](create-session-text-file.md) |
| downloadFolderAsZip | Zip a folder in the current session sandbox (default) or shared area and return a download URL. Use this when the user asks to download a directory as a single archive. By default attachOnlyZip=true, so intermediate generated files are removed from the attachment list and only the zip is attached. Set attachToChat=false if the zip should be generated without any chat attachment. Response guidance: do not paste raw download URLs in assistant text; generated files are auto-attached to the chat message. | [downloadFolderAsZip](download-folder-as-zip.md) |
| extractTar | Extract a tar archive into the session/shared file area with safe path validation. | [extractTar](extract-tar.md) |
| extractZip | Extract a zip archive into the session/shared file area with safe path validation. | [extractZip](extract-zip.md) |

### File System

| Tool | Description | Full page |
|---|---|---|
| fileExists | Check whether a file exists in the session/shared file area. | [fileExists](file-exists.md) |
| folderExists | Check whether a folder exists in the session/shared file area. | [folderExists](folder-exists.md) |
| createFolder | Create a directory in the current session sandbox (default) or shared area. Creates intermediate directories when necessary. | [createFolder](create-folder.md) |
| listFiles | List files/folders for a directory in the current session sandbox (default) or shared area. File entries include download URLs. | [listFiles](list-files.md) |
| readFile | Read a file from the current session sandbox (default) or shared area. Returns UTF-8 text content for text files and base64 for binary files. | [readFile](read-file.md) |
| writeBase64File | Write a binary file into the current session sandbox (default) or shared area from Base64 content. The incoming base64Content is decoded to raw bytes before writing to disk. Both standard Base64 and URL-safe Base64 are accepted automatically (no mode switch required). Set attachToChat=false for intermediate files that should not appear in the assistant attachment list. Response guidance: do not paste raw download URLs in assistant text; generated files are auto-attached to the chat message. | [writeBase64File](write-base64-file.md) |
| writeFile | Write a UTF-8 file into the current session sandbox (default) or shared area. Returns a direct download URL that can be rendered in chat attachments. Use this for generating markdown, text, JSON, code, or configuration files. Set attachToChat=false for intermediate files that should not appear in the assistant attachment list. Response guidance: do not paste raw download URLs in assistant text; generated files are auto-attached to the chat message. | [writeFile](write-file.md) |


### Text Files

| Tool | Description | Full page |
|---|---|---|
| getTextFileInfo | Inspect a text/log file without returning its full content. Use this first for large files to get size and line count before searching. | [getTextFileInfo](get-text-file-info.md) |
| readTextFileRange | Read a precise inclusive line range from a text/log file. Use after searchTextFile identifies an interesting region; avoids loading the entire file. | [readTextFileRange](read-text-file-range.md) |
| searchTextFile | Search very large text/log files line-by-line with bounded contextual windows around matches. Prefer this over full-file reads when looking for errors, IDs, protocol events, or timestamps. | [searchTextFile](search-text-file.md) |


### Knowledge

| Tool | Description | Full page |
|---|---|---|
| defineKnowledge | Persistently define a new knowledge article in the knowledge base. The base is a category name (e.g. 'Deployment', 'Troubleshooting'). Content is the free-text article. | [defineKnowledge](define-knowledge.md) |
| getKnowledge | Retrieve all knowledge base articles in a given category, sorted by creation date (newest first). | [getKnowledge](get-knowledge.md) |
| searchKnowledge | Search knowledge base articles by category and keyword. Returns matching articles with content, timestamps, and UUIDs. | [searchKnowledge](search-knowledge.md) |

### Meta

| Tool | Description | Full page |
|---|---|---|

| getDateTime | Return the current local system date and time, including timezone. | [getDateTime](get-date-time.md) |
| memory | Session key/value memory store. Use operation=set|get|list|delete to manage reusable context that is injected into future system prompts. | [memory](memory.md) |
| recordProgress | Persist a concise progress checkpoint to session memory for use in later turns. Use this after completing significant steps (e.g. host scanned, report generated, report sent). | [recordProgress](record-progress.md) |
| think | Log your reasoning or analysis mid-turn without ending the turn. Call this to express your thinking, then IMMEDIATELY invoke the next action tool. NEVER end a turn with only a think call. | [think](think.md) |

### Notifications

| Tool | Description | Full page |
|---|---|---|
| listNotificationLedgerEntries | Show paged notification delivery history with optional filters for status, destination, and provider. | [listNotificationLedgerEntries](list-notification-ledger-entries.md) |
| listNotificationProviders | List available notification providers and the address types each provider supports. | [listNotificationProviders](list-notification-providers.md) |
| sendNotification | Send a notification through a configured provider to an email address or phone number for internal or external recipients. | [sendNotification](send-notification.md) |
| summarizeNotificationLedger | Return notification delivery totals and grouped health statistics without listing every ledger row. | [summarizeNotificationLedger](summarize-notification-ledger.md) |

### Schema & Types

| Tool | Description | Full page |
|---|---|---|
| compileJavaType | Compile Java source code into a runtime type, save it, and make it available immediately in Vork. | [compileJavaType](compile-java-type.md) |
| discoverExportableTypes | List the Java types that Vork can export, including approved built-in types and runtime-created types. | [discoverExportableTypes](discover-exportable-types.md) |
| exportAllJavaTypeData | Export stored JSON data for every exportable entity type as a full snapshot. | [exportAllJavaTypeData](export-all-java-type-data.md) |
| exportJavaType | Export stored JSON data for one exportable type, either by record ID or as all records for that type. | [exportJavaType](export-java-type.md) |
| exportJavaTypeSource | Export the saved Java source code for a runtime-created custom type. | [exportJavaTypeSource](export-java-type-source.md) |
| getJavaTypeSource | Retrieve the saved Java source for a compiled type so you can review or update it safely. | [getJavaTypeSource](get-java-type-source.md) |
| getTypeSchema | Return a JSON schema view of a compiled type so you can see expected fields and data types. | [getTypeSchema](get-type-schema.md) |
| listEnumValues | List all allowed constant values for an enum type by its fully qualified name. | [listEnumValues](list-enum-values.md) |
| listJavaTypes | List all custom Java types that were compiled and saved in Vork. | [listJavaTypes](list-java-types.md) |

### Surface

| Tool | Description | Full page |
|---|---|---|
| getSurfaceAgentContracts | Return contracts for surface-assigned agents, including agentTemplateId and agent type. Call this before generating UI code that invokes surface agents. | [getSurfaceAgentContracts](get-surface-agent-contracts.md) |
| getSurfaceReflectionContracts | Return input/output contracts for reflections attached to the current surface session. Call this before generating UI code that invokes reflections. | [getSurfaceReflectionContracts](get-surface-reflection-contracts.md) |
| getSurfaceSkillContracts | Return contracts for skills attached to the current surface session, including groupId/skillId and output schema. Call this before generating UI code that invokes surface skills. | [getSurfaceSkillContracts](get-surface-skill-contracts.md) |

### Web

| Tool | Description | Full page |
|---|---|---|
| httpRequest | Send an HTTP request and return the response status code, headers, and body. Supports GET, POST, PUT, PATCH, DELETE, HEAD, and OPTIONS. Use this to interact with REST APIs, fetch web pages, or submit forms. For GET requests put query parameters in the URL. For POST/PUT/PATCH supply the body as a string and set the Content-Type header. Set responseMode=BINARY with saveToPath to download binary content into session/shared storage. The response body is truncated to 20 000 characters. | [httpRequest](http-request.md) |

## Runtime-generated tool families

These are also real tools in Vork, but their names and schemas are generated at runtime from records, not fixed in one static list.

- [Reflection-generated tools](runtime-reflection-tools.md)
- [Skill-generated tools](runtime-skill-tools.md)
- [MCP binding tools](runtime-mcp-tools.md)
