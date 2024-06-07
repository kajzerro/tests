import com.example.fileservice.service.FileService;
import org.springframework.stereotype.Service;

import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.StandardCopyOption;

@Service
public class LocalFileServiceImpl implements FileService {

    @Override
    public void uploadFile(Path path, String destination) {
        try {
            Files.copy(path, Path.of(destination), StandardCopyOption.REPLACE_EXISTING);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    @Override
    public void downloadFile(String source, Path destination) {
        try {
            Files.copy(Path.of(source), destination, StandardCopyOption.REPLACE_EXISTING);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    @Override
    public void deleteFile(String source) {
        try {
            Files.delete(Path.of(source));
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
